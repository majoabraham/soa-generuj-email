# soa-generuj-email

- vytvorene v Oracle JDeveloper 12c ako SOA project

- sluzba generuje email v tvare meno.priezvisko@domena - sluzi na podporu vytvarania emailov

- vytvorenie XML Schema - subor gen_email_MSG.xsd - sluzi pre komunikaciu pomocou sprav
	- vstupna sprava: genEmailRequest -> vstup -> meno: typ string, priezvisko: typ string, domena: typ string
	- vystupna sprava: genEmailResponse -> email: typ string

- pridany bussiness proces ako BPEL 2.0 komponent - popisuje bussiness proces - genEmailProcess.bpel
	- implementovany ako stateful service
	- web service
	- synchronny BPEL proces
	- sluzba genemailprocess_client je exponovana ako SOAP sluzba: vstup: genEmailRequest, vystup genEmailResponse
	- funkcionalita vytvorena cez priradenie AssignEmail
	
- opis procesu je vo WSDL
  - abstraktny WSDL genEmailProcess.wsdl
  - konkretny WSDL sa vytvori po nasadeni na aplikacny server
  
- na nasadenie pouzivam aplikacny server WebLogic Server 
	- enterprise manager u mna na http://localhost:7101/em
	
- po nasadeni konkretne WSDL je vygenerovane na serveri 
	- u mna http://localhost:7101/soa-infra/services/default/soa-generuj-email/genemailprocess_client_ep?WSDL
- a endpoint 
	- u mna http://localhost:7101/soa-infra/services/default/soa-generuj-email/genemailprocess_client_ep
	
- test je mozny priamo na aplikacnom serveri, ale neodporuca sa to, testujem pomocou nastroja SoapUI,
pricom projekt je SOAP projekt a vlozim konkretne WSDL
