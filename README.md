# Methodo

## Premièrement -> le statique

Je fais en sorte d'avoir mes composants dans des fichiers séparés, et je les affiche là où j'en ai besoin. Chaque composant est statique dans le sens où il affiche de lui-même son contenu, sans passer par les props

## Tester le passage de props

Identifier les infos ou les fonctions dont a besoin votre composant. Les faire passer depuis le parent, les récupérer dans le composant enfant et les afficher / exécuter là où il faut.

## Créer le state 
Je crée dans le state les datas dont ont besoin mes composants.
Dans un reducer, créer le state initial et une fonction qui ne fait rien d'autre qu'un switch qui return le state.

## Je relie mon composant à redux

Je crée un container, qui importe mon composant, et qui lui donne tous les props dont il a besoin (data ou fonctions -> infos du state ou dispatch d'une action).

je commence par créer des props dans le mapState, que je remplis pour de faux.

Pour les fonctions attendues par mon composant, je les donne dans le container, et je me contente d'un console.log.

## J'affiche mon container à la place du composant

C'est le container qui affiche le composant en lui donnant les props dont il a besoin, c'est donc lui que je dois afficher là où j'utilisais mon composant.


## Je relie mon state aux props du composant

Dans le mapStateToPros, je peux utiliser le state que je reçois en paramètre pour dire: Dans tel props je veux telle info du state

## Je relie la possibilité de dispatcher des actions aux props du composant

Pour le moment nos fonctions ne font qu'un console.log. Il faudrait plutôt dispatcher des actions pour déclencher des changements.

J'ai besoin de travailler dans 3 fichiers:

* action -> je décris les actions
* reducer -> je réagis aux actions
* container: j'émet les actions


 ### Je crée les actions

 Chaque action se matérialise par un type au minimum, et doit être un objet. Je crées des variables pour stocker les différents types d'actions de mon app, et je les exports pour pouvoir y réagir ailleurs.

 Je crée ensuite mes action creators. Des fonctions qui return un objet d'action, avec le bon type. Et si j'ai besoin de transmettre de la data au reducer, je peux également l'accrocher dans l'objet d'action que je fabrique (payload).

 ### Je réagis aux types d'actions

 Dans le reducer, j'importe les types auxquels je veux réagir, et dans le cas où le type d'une action est CECI, je modifie mon state comme CELA.


 ### J'émet mes actions.

 Le plus souvent, les actions sont émises depuis un container (fetchRecipes, checkAuth, inputChange).

 Dans les props qui contiennent des fonctions, je dispatch l'action qui correspond.

 ## Je relie mon app au monde exterieur

 Si des actions nécessitent d'aller chercher / donner des infos à un serveur par exemple, il faut que j'intercepte ces actions, pour y réagir et déclencer des requêtes par exemple.

 C'est le rôle du middleware redux.

 Un middleware recevra toutes les actions émises, et peut:

 * les laisser passer ou pas (en général, on laisse tout passer)
 * Si le type d'action m'intéresse, je peux déclencher une requête
 * Si la requête se passe bien
   * Je peux dispatcher une action pour informer mon reducer que j'ai reçu ceci ou cela
 * Sinon
   * Je peux dispatcher une action pour informer mon reducer que je n'ai pas reçu 
