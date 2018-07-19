---
title: 'Tutoriel : Azure Functions'
description: Utilisation de fonctions Azure dans Visual Studio pour Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 38FD2070-5151-482E-B0A9-993715128736
ms.openlocfilehash: 80c04182733204a18ee669d3851deab867cc56cd
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "33877330"
---
# <a name="tutorial-getting-started-with-azure-functions"></a>Tutoriel : Bien démarrer avec Azure Functions

Dans cet atelier, vous allez apprendre à créer des fonctions Azure à l’aide de Visual Studio pour Mac. Vous verrez également comment les intégrer à des tables de stockage Azure, qui figurent parmi les nombreux types de liaisons et de déclencheurs à la disposition des développeurs Azure Functions.

## <a name="objectives"></a>Objectifs

> [!div class="checklist"]
> * Créer et déboguer des fonctions Azure locales
> * Intégrer des fonctions à des ressources de stockage web et Azure
> * Orchestrer un flux de travail impliquant plusieurs fonctions Azure

## <a name="requirements"></a>Configuration requise

- Visual Studio pour Mac 7.5 ou ultérieur
- Un abonnement Azure (disponible gratuitement sur le site [https://azure.com/free](https://azure.com/free))

## <a name="exercise-1-creating-an-azure-functions-project"></a>Exercice 1 : Création d’un projet Azure Functions

1. Lancez **Visual Studio pour Mac**.

1. Sélectionnez **Fichier > Nouvelle solution**.

1. Dans la catégorie **Cloud > Général**, sélectionnez le modèle **Azure Functions**. Vous allez utiliser C# pour créer une bibliothèque de classes .NET qui héberge Azure Functions. Cliquez sur **Suivant**.

    ![Sélection du modèle Azure Functions](media/azure-functions-lab-image1.png)

1. Tapez **AzureFunctionsLab** dans le champ **Nom du projet**, puis cliquez sur **Créer**.

    ![Nommage et création d’un projet de fonction Azure](media/azure-functions-lab-image2.png)

1. Développez les nœuds dans le **Panneau Solutions**. Le modèle de projet par défaut inclut des références NuGet à une variété de packages AzureWebJobs, ainsi qu’au package Newtonsoft.Json. 

     Il comprend également trois fichiers : - **host.json** pour décrire les options de configuration globales pour l’hôte. - **local.settings.json** pour configurer les paramètres de service. 
        - Le modèle de projet crée également un HttpTrigger par défaut. Pour les besoins de cet atelier, supprimez le fichier **HttpTrigger.cs** du projet.

    Ouvrez **local.settings.json**. Il contient par défaut deux paramètres de chaîne de connexion vides.

    ![Panneau Solutions montrant le fichier local.settings.json](media/azure-functions-lab-image3.png)

## <a name="exercise-2-creating-an-azure-storage-account"></a>Exercice 2 : Création d’un compte de stockage Azure

1. Connectez-vous à votre compte Azure à l’adresse [https://portal.azure.com](https://portal.azure.com).
 
1. Sous la section **Favoris** située à gauche de l’écran, sélectionnez **Comptes de stockage** :

    ![Section Favoris du portail Azure montrant l’élément Comptes de stockage](media/azure-functions-lab-image4.png)

1. Sélectionnez **Ajouter** pour créer un compte de stockage :

    ![Bouton permettant d’ajouter un nouveau compte de stockage](media/azure-functions-lab-image5.png)

1. Entrez un nom global unique dans le champ **Nom** et réutilisez-le comme **Groupe de ressources**. Vous pouvez conserver tous les autres éléments par défaut.

    ![Détails du nouveau compte de stockage](media/azure-functions-lab-image6.png)

1. Cliquez sur **Créer**. La création d’un compte de stockage peut prendre quelques minutes. Vous recevrez une notification une fois l’opération terminée.

    ![Notification de la réussite du déploiement](media/azure-functions-lab-image7.png)

1. Sélectionnez le bouton **Accéder à la ressource** dans la notification.

1. Sélectionnez l’onglet **Clés d’accès**.

    ![Paramètre de clé d’accès](media/azure-functions-lab-image8.png)

1. Copiez la première **Chaîne de connexion**. Cette chaîne permet d’intégrer le stockage Azure à vos fonctions Azure par la suite.

    ![Informations pour la clé numéro 1](media/azure-functions-lab-image9.png)

1. Revenez à **Visual Studio pour Mac**, puis collez la chaîne de connexion complète comme paramètre **AzureWebJobsStorage** dans **local.settings.json**. Vous pouvez maintenant référencer le nom du paramètre dans les attributs des fonctions qui ont besoin d’accéder à ses ressources.

    ![Fichier de paramètres locaux avec clé de connexion entrée](media/azure-functions-lab-image10.png)

## <a name="example-3-creating-and-debugging-an-azure-function"></a>Exemple 3 : Création et débogage d’une fonction Azure

1. Vous êtes prêt à ajouter du code. Quand vous utilisez une bibliothèque de classes .NET, les fonctions Azure sont ajoutées comme méthodes statiques. Dans le **Panneau Solutions**, cliquez avec le bouton droit sur le nœud de projet **AzureFunctions**, puis sélectionnez **Ajouter > Ajouter une fonction** :

    ![Option Ajouter une fonction](media/azure-functions-lab-image11.png)

1. Dans la boîte de dialogue Nouvelle fonction Azure, sélectionnez le modèle Generic WebHook. Tapez **Add** dans le champ **Nom**, puis cliquez sur **OK** pour créer votre fonction :

    ![Boîte de dialogue Nouvelle fonction Azure](media/azure-functions-lab-image12.png)

1. En haut du nouveau fichier, ajoutez les directives **using** ci-dessous :

    ```csharp
    using Microsoft.Azure.WebJobs.Extensions.Http;
    using System.Web;
    using Microsoft.WindowsAzure.Storage.Table;
    ```
1. Supprimez la méthode `Run` existante et ajoutez la méthode ci-dessous à la classe comme fonction Azure :

    ```csharp
    [FunctionName("Add")]
    public static int Run(
    [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
    HttpRequestMessage req,
    TraceWriter log)
    {
        int x = 1;
        int y = 2;

        return x + y;
    }
    ```
1. Passons en revue la définition de la méthode élément par élément. 
    
    La première chose que vous voyez est l’attribut **FunctionName**. Celui-ci marque la méthode comme étant une fonction Azure. L’attribut désigne le nom public de la fonction. Le nom de l’attribut ne doit pas forcément correspondre au nom réel de la méthode.

    ![Nouvelle méthode Run avec l’attribut FunctionName mis en surbrillance](media/azure-functions-lab-image13.png)

1. Ensuite, la méthode est marquée comme étant une méthode publique statique (**public static**). Cette étape est obligatoire. Vous remarquez également que la valeur de retour est un **int**. Sauf indication contraire au moyen d’attributs de méthode, toute valeur de retour non void d’une fonction Azure est retournée au client sous forme de texte. Par défaut, elle est retournée au format **XML**, mais vous pourrez la retourner au format **JSON** plus loin dans cet atelier.

    ![Nouvelle méthode Run avec mise en surbrillance de l’initialisation de la méthode](media/azure-functions-lab-image14.png)

1. Le premier paramètre est marqué avec l’attribut **HttpTrigger**, ce qui indique que cette méthode est appelée par une requête HTTP. L’attribut spécifie également le niveau d’autorisation de la méthode, ainsi que les verbes pris en charge (uniquement **"GET"** dans ce cas). Vous pouvez éventuellement définir une **Route** qui substitue le chemin à la méthode et qui permet d’extraire automatiquement des variables du chemin. Comme **Route** a ici la valeur Null, le chemin à cette méthode est par défaut **/api/Add**.

    ![Nouvelle méthode Run avec mise en surbrillance du paramètre](media/azure-functions-lab-image15.png)

1. Le dernier paramètre de la méthode est un **TraceWriter** qui peut être utilisé pour journaliser les messages relatifs aux diagnostics et aux erreurs.

    ![Nouvelle méthode Run avec mise en surbrillance de TraceWriter](media/azure-functions-lab-image16.png)

1. Cliquez dans la marge de la ligne **return** de la méthode pour définir un point d’arrêt :

    ![Point d’arrêt défini au niveau de la ligne return](media/azure-functions-lab-image17.png)

1. Générez et exécutez le projet dans une session de débogage. Pour cela, appuyez sur **F5** ou sélectionnez **Exécuter > Démarrer le débogage**. Vous pouvez également cliquer sur le bouton **Exécuter**. Ces options effectuent toutes la même tâche. Le reste de cet atelier fait référence à **F5**, mais vous pouvez utiliser la méthode qui vous convient le mieux.

    ![Générer et exécuter le projet](media/azure-functions-lab-image18.png)

1. L’exécution du projet ouvre automatiquement l’application Terminal.

1. Le projet passe par un processus de détection des fonctions Azure basé sur des attributs de méthode et une convention de fichier, laquelle est traitée plus loin dans cet article. Dans ce cas, il détecte une seule fonction Azure et « génère » 1 fonction de travail.

    ![Sortie de fonction Azure dans Terminal](media/azure-functions-lab-image19.png)

1. Au bas des messages de démarrage, l’hôte Azure Functions affiche les URL des API des déclencheurs HTTP. Il ne doit y en avoir qu’une. Copiez cette URL et collez-la sous un nouvel onglet du navigateur.

    ![URL d’API de fonction Azure](media/azure-functions-lab-image20.png)

1. Le point d’arrêt doit se déclencher immédiatement. La requête web a été routée à la fonction et peut désormais être déboguée. Pointez avec la souris sur la variable **x** pour afficher sa valeur. 

    ![Point d’arrêt déclenché](media/azure-functions-lab-image21.png)

1. Supprimez le point d’arrêt en suivant la même méthode que celle utilisée plus haut pour l’ajouter (cliquez sur la marge ou sélectionnez la ligne et appuyez sur **F9**).

1. Appuyez sur **F5** pour poursuivre l’exécution.

1. Le navigateur affiche le résultat XML de la méthode. Comme prévu, l’opération d’addition codée en dur produit une somme plausible. Si vous voyez seulement « 3 » dans Safari, accédez à **Safari > Préférences > Avancées** et cochez la case **Afficher le menu Développement dans la barre de menus**. Ensuite, rechargez la page.

1. Dans **Visual Studio pour Mac**, cliquez sur le bouton **Arrêter** pour mettre fin à la session de débogage. Pour que les nouveaux changements entrent en vigueur, n’oubliez pas de redémarrer (arrêter, puis exécuter) la session de débogage.

    ![Option Arrêter le débogage](media/azure-functions-lab-image22.png)

1. Dans la méthode **Run**, remplacez les définitions **x** et **y** par le code ci-dessous. Ce code extrait les valeurs de la chaîne de requête de l’URL de manière à ce que l’opération d’addition puisse être exécutée dynamiquement en fonction des paramètres fournis.

    ```csharp
    var query = HttpUtility.ParseQueryString(req.RequestUri.Query);

    int x = int.Parse(query["x"]);

    int y = int.Parse(query["y"]);

    return x + y;
    ```
1. Exécutez l'application.

1. Revenez à la fenêtre du navigateur et ajoutez la chaîne `/?x=2&y=3` à l’URL. L’URL complète doit maintenant être `http://localhost:7071/api/Add?x=2&y=3`. Accédez à la nouvelle URL.

1. Le résultat doit à présent refléter les nouveaux paramètres. N’hésitez pas à exécuter le projet avec des valeurs différentes. Notez qu’aucune vérification des erreurs n’est effectuée. Tout paramètre non valide ou manquant génère donc une erreur.

1. Arrêtez la session de débogage.


## <a name="exercise-4-working-with-functionjson"></a>Exercice 4 : Utilisation de function.json

1.  Dans un exercice précédent, il est mentionné que Visual Studio pour Mac « génère » une fonction de travail pour la fonction Azure définie dans la bibliothèque. Cela vient du fait qu’Azure Functions n’utilise pas réellement les attributs de méthode au moment de l’exécution. Au lieu de cela, il utilise une convention de système de fichiers au moment de la compilation pour configurer où et comment les fonctions Azure sont mises à disposition. Dans le **Panneau Solutions**, cliquez avec le bouton droit sur votre nœud de projet et sélectionnez **Révéler dans le Finder**.

     ![Option Révéler dans le Finder](media/azure-functions-lab-image23.png)

1. Descendez dans le système de fichiers jusqu’à ce que vous arriviez à **bin/Debug/netstandard2.0**. Vous devriez trouver un dossier nommé **Add**. Ce dossier a été créé pour correspondre à l’attribut de nom de fonction dans le code C#. Développez le dossier Add pour révéler un fichier **function.json** unique. Ce fichier est utilisé par le runtime pour héberger et gérer la fonction Azure. Pour les autres modèles de langage ne prenant pas en charge la compilation (comme Script C# ou JavaScript), vous devez créer et tenir à jour manuellement ces dossiers. Pour les développeurs C#, ils sont automatiquement générés à partir des métadonnées d’attribut au moment de la génération. Cliquez avec le bouton droit sur le fichier **function.json** et sélectionnez-le pour l’ouvrir dans Visual Studio.

    ![function.json dans le répertoire de fichiers](media/azure-functions-lab-image24.png)

1. Si vous avez suivi les étapes précédentes de ce tutoriel, vous devez avoir des connaissances de base des attributs C#. Le code JSON qui suit doit donc vous sembler familier. Toutefois, quelques éléments n’ont pas été abordés dans les exercices précédents. Par exemple, chaque liaison (**binding**) doit avoir une **direction** définie. Comme vous l’aurez deviné, **"in"** signifie que le paramètre est une entrée, tandis que **"out"** indique que le paramètre est une valeur de retour (par le biais de **$return**) ou un paramètre **out** de la méthode. Vous devez également spécifier le **scriptFile** (par rapport à cet emplacement final) et la méthode **entryPoint** (publique et statique) dans l’assembly. Au cours des prochaines étapes, vous allez ajouter un chemin de fonction personnalisé à l’aide de ce modèle. Vous devez donc copier le contenu de ce fichier dans le Presse-papiers.

    ![Fichier function.json ouvert dans Visual Studio pour Mac](media/azure-functions-lab-image25.png)

1. Dans le **Panneau Solutions**, cliquez avec le bouton droit sur le nœud de projet **AzureFunctions**, puis sélectionnez **Ajouter > Nouveau dossier**. Nommez le nouveau dossier **Adder**. Selon la convention par défaut, le nom de ce dossier définit le chemin à l’API (par exemple, **api/Adder**).

    ![Option Nouveau dossier](media/azure-functions-lab-image26.png)

1. Cliquez avec le bouton sur le dossier **Adder** et sélectionnez **Ajouter > Nouveau fichier**.

    ![Option Nouveau fichier](media/azure-functions-lab-image27.png)

1. Sélectionnez la catégorie **Web** et le modèle **Fichier JSON vide**. Tapez **function** dans le champ **Nom**, puis cliquez sur **Nouveau**.

    ![Option Fichier JSON vide](media/azure-functions-lab-image28.png)

1. Collez le contenu de l’autre fichier **function.json** (créé au cours de l’étape 3) pour remplacer le contenu par défaut du fichier que vous venez de créer.

1. Supprimez les lignes suivantes dans la partie supérieure du fichier JSON :

    ```json
    "configurationSource":"attributes",
    "generatedBy":"Microsoft.NET.Sdk.Functions-1.0.13",
    ```

1. À la fin de la première liaison (après la ligne **"name": "req"**), ajoutez les propriétés ci-dessous. N’oubliez pas d’ajouter une virgule à la ligne précédente. Cette propriété se substitue à la racine par défaut. Elle extrait ainsi les paramètres **int** du chemin d’accès et les place dans les paramètres de méthode nommés **x** et **y**.

    ```json
    "direction": "in",
    "route": "Adder/{x:int?}/{y:int?}"
    ```

1. Ajoutez une autre liaison sous la première. Cette liaison gère la valeur de retour de la fonction. N’oubliez pas d’ajouter une virgule à la ligne précédente :

    ```json
    {
    "name": "$return",
    "type": "http",
    "direction": "out"
    }
    ```

1. Changez également la propriété **entryPoint** située en bas du fichier de manière à ce qu’elle utilise une méthode appelée **« Add2 »**, comme indiqué ci-dessous. Vous pouvez donc constater que le chemin **api/Adder...** peut mapper à une méthode appropriée avec un nom quelconque (**Add2** ici).

    ```json
    "entryPoint": "<project-name>.<function-class-name>.Add2"
    ```

1. Votre fichier **function.json** doit ressembler au code JSON suivant :

    ```json
    {
    "bindings": [
        {
        "type": "httpTrigger",
        "methods": [
            "get"
        ],
        "authLevel": "function",
        "direction": "in",
        "name": "req",
        "route": "Adder/{x:int?}/{y:int?}"
        },
        {
        "name": "$return",
        "type": "http",
        "direction": "out"
        }
    ],
    "disabled": false,
    "scriptFile": "../bin/AzureFunctionsProject.dll",
    "entryPoint": "AzureFunctionsProject.Add.Add2"
    }
    ```

1. Pour que tout fonctionne correctement, la dernière étape consiste à charger Visual Studio pour Mac de copier ce fichier dans le même chemin relatif du répertoire de sortie chaque fois qu’il change. Veillez à ce que le fichier soit sélectionné, puis choisissez l’onglet des propriétés dans la barre de droite. Ensuite, pour **Copier dans le répertoire de sortie**, sélectionnez **Copier si plus récent** :

    ![Options des propriétés pour le fichier json](media/azure-functions-lab-image30.png)

1. Dans **Add.cs**, remplacez la méthode `Run` (attribut inclus) par la méthode suivante pour obtenir la fonction attendue. Elle est très similaire à `Run`, mais elle n’utilise aucun attribut et contient des paramètres explicites pour **x** et **y**.

    ```csharp
    public static int Add2(
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        return x + y;
    }
    ```
1. Appuyez sur **F5** pour générer et exécuter le projet.

1. À mesure que la build s’achève et que la plateforme tourne, une deuxième route mappée à la méthode qui vient d’être ajoutée est désormais disponible pour les requêtes :

    ![URL pour les fonctions HTTP](media/azure-functions-lab-image31.png)

1. Revenez à la fenêtre du navigateur et accédez à **http://localhost:7071/api/Adder/3/5**.

1. La méthode aboutit une fois de plus, tirant (pull) les paramètres du chemin et produisant une somme.

1. Revenez à **Visual Studio pour Mac** et terminez la session de débogage.

## <a name="exercise-5-working-with-azure-storage-tables"></a>Exercice 5 : Utilisation des tables de stockage Azure

Les services que vous générez sont souvent beaucoup plus complexes que ceux que nous avons générés jusqu’à présent, et leur exécution nécessite des ressources importantes en termes de temps et/ou d’infrastructure. Dans ce cas, il peut être judicieux d’accepter les demandes qui sont en file d’attente de traitement quand les ressources deviennent disponibles, ce qu’il est possible de faire avec Azure Functions. Dans d’autres cas, vous pouvez stocker les données de manière centralisée. Pour y parvenir rapidement, utilisez des tables de stockage Azure. 

1. Ajoutez la classe ci-dessous à **Add.cs**. Placez-la dans l’espace de noms, mais à l’extérieur de la classe existante.

    ```csharp
    public class TableRow : TableEntity
    {
        public int X { get; set; }
        public int Y { get; set; }
        public int Sum { get; set; }
    }
    ```
1. Dans la classe **Add**, ajoutez le code ci-dessous pour introduire une autre fonction. Notez que celle-ci est sans précédent dans la mesure où elle n’implique aucune réponse HTTP. La dernière ligne retourne un nouveau **TableRow** rempli avec des informations de clé qui permettront de le récupérer facilement par la suite (**PartitionKey** et **RowKey**), ses paramètres et la somme. Le code dans la méthode utilise également **TraceWriter** pour savoir plus facilement à quel moment la fonction s’exécute.

    ```csharp
    [FunctionName("Process")]
    [return: Table("Results")]
    public static TableRow Process(
        [HttpTrigger(AuthorizationLevel.Function, "get",
            Route = "Process/{x:int}/{y:int}")]
        HttpRequestMessage req,
        int x,
        int y,
        TraceWriter log)
    {
        log.Info($"Processing {x} + {y}");
    
        return new TableRow()
        {
            PartitionKey = "sums",
            RowKey = $"{x}_{y}",
            X = x,
            Y = y,
            Sum = x + y
        };
    }
    ```
1. Appuyez sur **F5** pour générer et exécuter le projet.

1. Sous l’onglet du navigateur, accédez à **http://localhost:7071/api/Process/4/6**. Un autre message est placé dans la file d’attente, ce qui doit aboutir à l’ajout d’une nouvelle ligne à la table.

1. Revenez au **Terminal** et observez la requête entrante **4 + 6**.

    ![Sortie du terminal montrant la requête d’addition](media/azure-functions-lab-image32.png)

1. Revenez au navigateur pour actualiser la requête à la même URL. Cette fois, vous devriez voir une erreur après la méthode **Process**. Cette erreur vient du fait que le code tente d’ajouter une ligne à la table Stockage Table Azure à l’aide d’une combinaison clé de partition/clé de ligne qui existe déjà.

    ``` 
    System.Private.CoreLib: Exception while executing function: Process. Microsoft.Azure.WebJobs.Host: Error while handling parameter $return after function returned:. Microsoft.Azure.WebJobs.Host: The specified entity already exists.
    ```

1. Mettez fin à la session de débogage.

1. Pour atténuer l’erreur, ajoutez le paramètre suivant à la définition de méthode immédiatement avant le paramètre **TraceWriter**. Ce paramètre charge la plateforme Azure Functions pour tenter de récupérer un **TableRow** à partir de la table **Results** sur le **PartitionKey** utilisé pour stocker les résultats. Toutefois, un tour de magie se produit quand vous constatez que **RowKey** est généré dynamiquement en fonction des autres paramètres **x** et **y** pour la même méthode. Si cette ligne existe déjà, **tableRow** l’a comme valeur au début de la méthode, sans aucun travail supplémentaire de la part du développeur. Si la ligne n’existe pas, il a simplement la valeur Null. Ce niveau d’efficacité permet aux développeurs de concentrer leurs efforts sur ce qui compte le plus, à savoir la logique métier, et non l’infrastructure.

    ```csharp
    [Table("Results", "sums", "{x}_{y}")]
    TableRow tableRow,
    ```
1. Ajoutez le code ci-dessous au début de la méthode. Si **tableRow** n’est pas Null, nous avons déjà les résultats de l’opération faisant l’objet d’une requête et nous pouvons les retourner immédiatement. Sinon, la fonction continue comme avant. Même s’il ne s’agit peut-être pas de la meilleure façon de retourner les données, vous pouvez orchestrer des opérations extrêmement sophistiquées sur plusieurs niveaux scalables avec très peu de code.

    ```csharp
    if (tableRow != null)
    {
        log.Info($"{x} + {y} already exists");
        return null;
    }
    ```
1. Appuyez sur **F5** pour générer et exécuter le projet.

1. Sous l’onglet du navigateur, actualisez l’URL à l’adresse **http://localhost:7071/api/Process/4/6**. Étant donné que la ligne de table pour cet enregistrement existe, elle doit être retournée immédiatement et sans erreur. Comme il n’y a pas de sortie HTTP, vous pouvez voir la sortie dans le Terminal.

    ![Sortie du Terminal montrant que la ligne de la table existe déjà](media/azure-functions-lab-image33.png)

1. Changez l’URL pour refléter une combinaison qui n’a pas encore été testée, par exemple **http://localhost:7071/api/Process/5/7**. Notez le message dans le Terminal qui indique que la ligne de table est introuvable (comme prévu).

    ![Sortie du Terminal montrant un nouveau processus](media/azure-functions-lab-image34.png)

1. Revenez à **Visual Studio pour Mac** et mettez fin à la session de débogage.

<!--
1. Finally, let's take a look at what it's like to work with multiple input records. Rather than specify a specific **TableRow**, you can request an **IQueryable<TableRow>** using the same attributes, and the runtime will fill it with the appropriate resource you need. Add the code below to create a **List** function that lists all items that currently exist in the Azure table we've been working with. Also note that we're specifying that the MIME type of the response is **application/json**, so the runtime will automatically render as JSON. 

    ```csharp
    [FunctionName("List")]
    public static HttpResponseMessage List(
        [HttpTrigger(AuthorizationLevel.Function, "get", Route = null)]
        HttpRequestMessage req,
        [Table("Results", "sums")]
        IQueryable<TableRow> table,
        TraceWriter log)
    {
        return req.CreateResponse(HttpStatusCode.OK, table, "application/json");
    }
    ```
1. Press **F5** to build and run the project.

1. In the browser tab, navigate to **http://localhost:7071/api/List**. This should pull down the list of all items in the Azure table and render it as JSON.

    ![](https://user-images.githubusercontent.com/3944468/29033725-be9d5a5e-7b4a-11e7-8b55-df0a200b6320.png)
-->

## <a name="summary"></a>Récapitulatif

Dans cet atelier, vous avez appris à créer des fonctions Azure à l’aide de Visual Studio pour Mac.

