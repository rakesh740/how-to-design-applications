# architechture description

 in bengali through a story:    ekta gmail type app banate hobe tar jonno backend architechture ta design korte hobe prothomoto ki ki feature thakbe seta likhe nite hobe tar por ek ekta feature er description r deep e bojhate hobe, banglai likhchi jate subidhe hoi.

 features:

 1. profile toiri kora
 2. profile authenticate kora / porichoi proman kora jate ek jon onno jon er profile byabohar na korte pare.
 3. email pathano nijer profile theke onno profile e
 4. email e attachment pathano / attachement dekha ba download kora reciever er
 5. spam filter kora email gulo k.  
 6. mail gulo k sothik vabe categorize kora
 7. onno domain er mail recieve kora / onno domain e mail send kora.

ebar  feature gulo k priority onusare ektar por ekta explain korte hobe.

## profile toiri kora

- ekjon user mobile/web use kore profile toiri korbe

    type user struct {
        userid *@gmail.com string
        password string
        Name string
        phone number
    }
ekta HTTP post request use kore profile toiri korbe jekhane uporer structure send kora jai - store kora hobe ekta single table a jekhane userid primary id ebong unique hobe. METHOD: createProfile(user)

- user tarpor otp diye nijer phone number ebong email verify korte hobe. verified ebong non-verified email er difference er jonno ekta bool value use kora jete pare. verifyPhonehumber(userid, otp)

## service modules

ek ekta module ek ekta service provide korbe

- profile service
- authentication service
- mail service
- analytics service

sob client (browser/ app) gulo ekta gateway er sathe connect korbe, request payload read kore particular service e forward korbe. etar jonno gateway te service discovery add korte hobe (kon service kon machine ba ip te ache seta jante hobe nahole kon request kon service e forward korte hobe gateway jante parbe na). service discovery module ta gateway tei kora jai kintu eta k onno ekta separate module e rakhle subidhe jate gateway er opor responsibility kome. ekta service registry module add kora jai er jonno - ete ki hobe :

   `client -> req to gateway -> call service registry to fetch latest available machines IPs -> response to gateway -> gateway forwards the requests to those IPs/ machines -> machine handles the service`

## service registry

- service registry module er advantage hocche j ekta jaigai sob module nijer available IP add kore debe jate gateway ekta distributed service holeu sob gateway ekta service registry connect kore fetch korte parbe.
- service registry heartbeat send kore sob machine gulor health check korbe r kono module IP down hole nijer registry update korlei sob gateway otar byapar e jante parbe
- ekhane service registry ekta bottle neck / onnano service k slow kore dite pare karon jodi sob request gateway theke service registry jai tarpor abar oi request forward korte hoi oi to particular module IP. ete extra round trip to service registry add hocche prottekta request er jonno.
- ei extra request komanor jonno ekta cache rakha jai gateway te jate besir vag request gateway nijer cache fetch korei request
correct IP te forward korte parbe bar bar service registry request korte hobe na. kintu extra cache rakhar problem hocche cache jate stale/purono na hoye jai.
- gateway te service registry er cache update korar daitto service registry er opor. jodi kono service machine down hoyeche ki na seta heartbeat er sahajje dekhte hobe, jodi down hoi tahole service registry database e update korte hobe tarpor oi updated data send korte hobe to gateway, gateway er cache update korar jonno.
- notun service add hole service age nijeke service registry te register korbe
  add      `service name   |   machine ips` to the table

## gateway

gateway ekta reverse proxy er moto:

- jeta client to server connection handle kore 
- external client request internal server request e convert/translate kore.
- DDoS attack theke bachai internal system k,
- spam IP gulo mark kore rate limitting kore
- IP blocklist kore 

 /// sob description gulo sobai buhte parbe na kintu ekhon kintu onekei term gulo janlei bujhbe.

## authentication service

user der password toiri korte hobe tader user id er jonno, ei password store thakbe hashed kore server e. jokhon user login korbe ei user nijer userid r password send korbe jeta authentication service verify korbe. sudu matro authentication er por e user account use korte parbe. ebar problem hocche protita action er jonno ki userid password verify korbo ? kora jai kintu eta ektu costly karon database theke saved password fetch kore r user er send kora password k hash kore compare kora somoy sapekkho, amra time er problem ta storage diye solve korte pari - first bas login korar somoi user er userid er jonno ekta session token create kora jai. oi user oi browser theke joto bar request send korbe tar sathe ei token ta send korbe. ebar sudu ekta cache rakhlei holo gateway te jekhane sudu token match korlei authenticated user . r token match na korle ba token cache e na thaklei user logout hoye jabe. secuirty purpose er jonno token er time to live/ TTL/ expiry time set kore rakhte hobe.
