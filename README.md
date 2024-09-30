## Exercice d'application des principes SOLID
### Gestion de maison connectée

Dans cet exercice, vous devez concevoir un **système de gestion d'une maison connectée** intégrant un **système de gestion des utilisateurs avec rôles**, un **système de log** pour tracer toutes les actions effectuées sur les dispositifs, ainsi qu'un **système d'alarme** pour déclencher des actions automatiques lorsque certaines conditions sont remplies (comme le dépassement d'une température).

L'objectif est de créer un **diagramme de classes** qui respecte les **principes SOLID**, tout en intégrant la gestion d’utilisateurs avec différents rôles, un système de logs pour tracer les actions, et un système d'alarme capable de surveiller et de réagir à des événements spécifiques.

----------

### Contexte

* **Dispositifs intelligents** :

    -   **Lumières intelligentes** : peuvent être allumées et éteintes et retourner leur état actuel.
    -   **Thermostats** : peuvent régler une température et surveiller les dépassements de seuil.
    -   **Serrures de portes** : peuvent être verrouillées et déverrouillées et retourner leur état actuel.
    -   **Caméras de sécurité** : peuvent être activées et désactivées pour enregistrer des vidéos.
-  **Rôles d'utilisateur** :

    -   **Admin** : Peut tout gérer.
    -   **Utilisateur standard** : Peut gérer les lumières et les thermostats.
    -   **Invité** : Peut uniquement gérer les lumières.
-  **Système de logs** :

    -   Chaque action effectuée par un utilisateur doit être enregistrée dans un journal qui détaille l’utilisateur ayant effectué l’action, le dispositif concerné, et l’action réalisée à un moment donné (par exemple : "Lumière allumée par Admin à 12h25, le 01/10/2024").
-  **Système d'alarme** :

    -   Le système d'alarme doit surveiller les dispositifs et déclencher des actions spécifiques lorsque certaines conditions sont remplies. Par exemple, si la température dépasse un seuil donné, une alarme doit être déclenchée et des actions doivent être réalisées (comme la coupure automatique des appareils énergivores).

----------

### Contraintes liées aux principes SOLID:

-  **Principe de responsabilité unique (SRP)** : Le système de log doit être séparé de la gestion des dispositifs. Le système d’alarme doit être responsable de surveiller les événements spécifiques (comme la température).

-  **Principe ouvert/fermé (OCP)** : Le système doit permettre d'ajouter de nouveaux dispositifs, rôles, ou événements surveillés (comme une alarme incendie) sans modifier les classes existantes.

-  **Principe de substitution de Liskov (LSP)** : Les classes concrètes doivent pouvoir être substituées par leurs abstractions respectives sans causer de dysfonctionnements dans le système.

-  **Principe de ségrégation des interfaces (ISP)** : Chaque dispositif doit implémenter uniquement les interfaces correspondant à ses capacités. Par exemple, une lumière ne doit pas implémenter d’interface de gestion de la température.

-  **Principe d'inversion de dépendances (DIP)** : Les classes de haut niveau (par exemple, le contrôleur de maison) doivent dépendre d’abstractions plutôt que de classes concrètes, notamment pour la gestion des utilisateurs et des logs.


----------

### Instructions :

**Étape 1 : Création des interfaces pour les dispositifs**  
Créez des interfaces pour les dispositifs (`Switchable`, `Lockable`, `TemperatureControllable`), comme dans les exercices précédents. Ces interfaces doivent permettre la gestion des actions des différents dispositifs intelligents.

**Étape 2 : Gestion des utilisateurs et rôles**  
Implémentez les rôles d'utilisateur (`Admin`, `StandardUser`, `Guest`) avec des permissions spécifiques. Chaque rôle doit pouvoir contrôler les dispositifs dans les limites de ses droits.

**Étape 3 : Ajout du système de logs**  
Créez une classe `Logger` qui sera responsable de tracer chaque action effectuée par les utilisateurs. Chaque action (comme "Lumière allumée") doit être enregistrée avec des informations sur l'utilisateur et le dispositif concerné.

**Étape 4 : Système d'alarme**  
Créez une classe `AlarmSystem` qui surveille des événements (comme le dépassement de la température d'un thermostat) et déclenche des actions automatiques lorsqu'une condition est remplie. Vous pouvez simuler l’alarme en imprimant un message ou en activant/désactivant des dispositifs spécifiques en réponse à l’alarme.

**Étape 5 : Intégration dans le contrôleur de maison**  
Le `SmartHomeController` doit intégrer la gestion des utilisateurs, des dispositifs, du système de logs, et du système d’alarme, tout en respectant les principes SOLID.