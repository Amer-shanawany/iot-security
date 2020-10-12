# Abstract

Een labfarm is een onafhankelijk werkende unit waarin planten op basis van hydrocultuur gekweekt worden. Het verbruik van de noodzakelijke voedingstoffen, water en licht voor een goede groei van de planten worden digitaal aangestuurd. Sensoren – vochtigheid en temperatuur – maken het mogelijk om op basis van deze factoren de aansturing te regelen. Dit systeem werkt volledig autonoom maar kan ook op afstand geregeld worden.

Om de planten op afstand te monitoren is in de labfarm een XY-systeem geïmplementeerd. Een camera kan naar een XY-positie worden bewogen en een opname nemen van de plant op die positie. Deze opname wordt samen met datum en tijd opgeslagen in een NoSQL-database (bv. Firebase) voor verdere verwerking. 

De controllers van de sensoren en verbruiksstoffen en het XY-systeem van de labfarm worden draadloos aangestuurd door een Google Coral Cluster. Meerdere labfarms – eventueel op verschillende locaties – kunnen simultaan worden gemonitored/bestuurd. Door middel van AI kan de cluster detecteren of een plant zich in een goede of slechte conditie bevind en op basis daarvan autonoom de controller van de verbruiksstoffen aansturen. Door middel van een webinterface (bv. Angular) is het ook mogelijk om de labfarm manueel op afstand aan te sturen en te monitoren.

![Abstract](/img/abstract.png)

