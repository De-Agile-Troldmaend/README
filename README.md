# README
Her finder du vores README
_____________________________

Kære Henrik,

Vi har fået team 2 delen til at virke lokalt. Vi har altså en Maintenancecontroller og kan poste en Workshoprequest. Vi kan sende og recieve med rabbitmq, og får requests delt op i 2 topics, repair og service. Vi kan lave en "GetAllRepair" og får repair opgaver frem, det samme virker på "GetAllService". 

Vi er klar over at vores navngivning ikke blev god.

Efter vi har containerized og lavet docker compose, kan vi ikke længere lavet vores get. Post'en gemmes ikke korrekt i en CSV-fil. 

Vi fik Loki & Grafana til at virke på taxabooking.

AuthenticationService er lavet og connected til MongoDB. Vehicle service er sat op, image-delen er ikke færdiggjort.
___________________________________________________

Vi har nået følgende: 
- Continous integration: Github actions, DockerHub
	- Lidt arbejde på Kanban inde på Github Boards
- Semantisk versionering: Container tags
- Authentication & Sikkerhed: JWT


Vi har ikke nået/fokuseret på følgende: 
- Semantisk versionering - (Kun lidt containertags)
- Alt Unit test 
- Docker network (kun fælles network for team 2) 
- Api-gateway og Load-balancer
- NLog, Loki & Grafana for worker & Maintenance
____________________________________________________
Testdata:
POST til Maintenanceservice 1 til hver Opgavetype¨
http://localhost:5070/Maintenance
{
    "Id": 1,
    "Beskrivelse": "Olieskift",
    "OpgaveType": 1,
    "IndsenderNavn": "Hans Hansen"
}
{
    "Id": 2,
    "Beskrivelse": "Hjulophæng defekt",
    "OpgaveType": 2,
    "IndsenderNavn": "Jens Larsen"
}

POST til Vehicleservice: Http Post
http://localhost:5038/Vehicle
{
  "id": {},
  "vehicleId": 3,
  "mærke": "Tesla",
  "model": "Y",
  "registreringsnummer": "AY83478",
  "servicehistorik": [
    {
      "serviceId": 3,
      "serviceDato": "2023-04-20T08:52:33.638Z",
      "serviceBeskrivelse": "Nye bremseskriver og olieskift",
      "værkstedansvarlig": "Peter"
    }
  ],
  "kilometerstand": 0,
  "billedehistorik": [
    {
      "placering": "/images/3.jpg",
      "dato": "2023-04-20T08:52:33.638Z",
      "beskrivelse": "bremseskiver",
      "personNavn": "Peter"
    }
  ]
}

Mvh. fire fuldstændigt færdige Troldmænd.
