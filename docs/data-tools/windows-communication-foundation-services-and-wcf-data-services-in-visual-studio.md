---
title: Windows Communication Foundation et WCF Data Services
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: b9f2202c96799fcc2e258e79f050d15fb474d0aa
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305505"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Services Windows Communication Foundation et services de données WCF dans Visual Studio

Visual Studio fournit des outils pour travailler avec Windows Communication Foundation (WCF) et WCF Data Services, les technologies Microsoft pour la création d’applications distribuées. Cette rubrique fournit une introduction aux services à partir d’un point de vue de Visual Studio. Pour obtenir la documentation complète, consultez [WCF Data Services 4.5](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>Nouveautés WCF ?

Windows Communication Foundation (WCF) est une infrastructure unifiée pour la création d’applications distribuées sécurisées, fiables, transactionnelles et interopérables. Il remplace les anciennes technologies de communication entre processus tels que les services web ASMX, .NET Remoting, Enterprise Services (DCOM) et MSMQ. WCF réunit les fonctionnalités de toutes ces technologies dans un modèle de programmation unifié. Cela simplifie l’expérience de développement d’applications distribuées.

### <a name="what-are-wcf-data-services"></a>Que sont les Services de données WCF

WCF Data Services est une implémentation du protocole OData (Open Data) standard.  WCF Data Services vous permet de qu'exposer des données tabulaires en tant qu’ensemble d’API REST, ce qui vous permet de retourner des données à l’aide de verbes HTTP standard tels que GET, post-traitement, PUT ou DELETE. Sur le côté serveur, WCF Data Services sont en cours remplacées par [API Web ASP.NET](http://www.asp.net/web-api) pour la création de services OData. La bibliothèque de client WCF Data Services continue d’être un bon choix pour consommer des services OData dans une application .NET à partir de Visual Studio (**projet** > **ajouter une référence de Service**). Pour plus d’informations, consultez [WCF Data Services 4.5](http://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>Modèle de programmation WCF

Le modèle de programmation WCF est basé sur la communication entre deux entités : un service WCF et un client WCF. Le modèle de programmation est encapsulé dans le <xref:System.ServiceModel> espace de noms dans le .NET Framework.

### <a name="wcf-service"></a>Service WCF

Un service WCF est basé sur une interface qui définit un contrat entre le service et le client. Il est marqué avec un <xref:System.ServiceModel.ServiceContractAttribute> d’attribut, comme illustré dans le code suivant :

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

Vous définissez les fonctions ou méthodes qui sont exposées par un service WCF en les marquant avec une <xref:System.ServiceModel.OperationContractAttribute> attribut.

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

En outre, vous pouvez exposer les données sérialisées en marquant un type composite avec un <xref:System.Runtime.Serialization.DataContractAttribute> attribut. Cela permet la liaison de données dans un client.

Une fois une interface et ses méthodes sont définies, elles sont encapsulées dans une classe qui implémente l’interface. Une seule classe de service WCF peut implémenter plusieurs contrats de service.

Un service WCF est exposé pour la consommation par l’intermédiaire de ce qui est appelée un *point de terminaison*. Le point de terminaison fournit le seul moyen de communiquer avec le service ; Vous ne pouvez pas accéder au service via une référence directe comme vous le feriez avec d’autres classes.

Un point de terminaison se compose d’une adresse, une liaison et un contrat. L’adresse définit où se trouve le service ; Cela peut être une URL, une adresse FTP, ou un réseau ou le chemin d’accès local. Une liaison définit la façon dont vous communiquez avec le service. Les liaisons WCF fournissent un modèle polyvalent pour spécifier un protocole tel que HTTP ou FTP, un mécanisme de sécurité telles que l’authentification Windows ou les noms d’utilisateur et mots de passe et bien plus encore. Un contrat inclut les opérations qui sont exposées par la classe de service WCF.

Plusieurs points de terminaison peuvent être exposées pour un seul service WCF. Cela permet aux différents clients communiquer avec le même service de différentes façons. Par exemple, un service bancaire peut fournir un point de terminaison pour les employés et un autre pour les clients externes, chacun utilisant une autre adresse, liaison, et/ou de contrat.

### <a name="wcf-client"></a>Client WCF (WCF client)

Un client WCF se compose d’un *proxy* qui permet à une application communiquer avec un service WCF et un point de terminaison qui correspond à un point de terminaison défini pour le service. Le proxy est généré côté client dans le *app.config* de fichiers et inclut des informations sur les types et les méthodes qui sont exposées par le service. Pour les services qui exposent plusieurs points de terminaison, le client peut sélectionner celui qui convient le mieux à ses besoins, par exemple, pour communiquer sur HTTP et utiliser l’authentification Windows.

Après la création d’un client WCF, vous référencez le service dans votre code comme vous le feriez pour tout autre objet. Par exemple, pour appeler le `GetData` méthode présentée précédemment, vous devez écrire le code qui ressemble à ceci :

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Outils WCF dans Visual Studio

Visual Studio fournit des outils pour vous aider à créer des services WCF et des clients WCF. Pour une procédure pas à pas qui montre les outils, consultez [procédure pas à pas : création d’un service WCF simple dans les Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>Créer et tester les services WCF

Vous pouvez utiliser les modèles WCF Visual Studio en tant que base pour créer rapidement votre propre service. Vous pouvez ensuite utiliser l’hôte de Service WCF et le Client Test WCF pour déboguer et tester le service. Ces outils fournissent un cycle de test et le débogage rapide et pratique entre eux et éliminent la nécessité de valider un modèle d’hébergement à un stade précoce.

#### <a name="wcf-templates"></a>Modèles WCF

Modèles WCF Visual Studio fournissent une structure de classe de base pour le développement de service. Plusieurs modèles WCF sont disponibles dans le **ajouter un nouveau projet** boîte de dialogue. Citons notamment WCF service lLibrary projets, des sites Web de service WCF et des modèles d’élément de Service WCF.

Lorsque vous sélectionnez un modèle, les fichiers sont ajoutés pour un contrat de service, une implémentation de service et une configuration de service. Tous les attributs nécessaires sont déjà ajoutés, création d’un type de « Hello World » simple du service, et vous ne disposait pas d’écrire du code. Est, bien sûr, voulez-vous ajouter du code pour fournir des fonctions et méthodes pour votre service de monde réel, mais les modèles fournissent la Fondation de base.

Pour en savoir plus sur les modèles WCF, consultez [modèles WCF Visual Studio](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>Hôte de service WCF

Lorsque vous démarrez le débogueur Visual Studio (en appuyant sur **F5**) pour un projet de service WCF, l’outil hôte de Service WCF est démarré automatiquement pour héberger le service localement. Hôte de Service WCF énumère les services dans un projet de service WCF, charge la configuration du projet et instancie un hôte pour chaque service qu’il trouve.

En utilisant l’hôte de Service WCF, vous pouvez tester un service WCF sans écrire de code supplémentaire ou se limiter à un hôte spécifique pendant le développement.

Pour en savoir plus sur l’hôte de Service WCF, consultez [hôte de service WCF (WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>Client test WCF

L’outil Client Test WCF vous permet d’entrer des paramètres de test, envoyer ces entrées à un service WCF et afficher la réponse que le service renvoie. Il fournit un expérience de test lorsque vous la combinez avec l’hôte de Service WCF de service pratique. L’outil de recherche dans les *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* dossier.

Quand vous appuyez sur **F5** pour déboguer un projet de service WCF, le Client Test WCF s’ouvre et affiche une liste de points de terminaison de service qui sont définis dans le fichier de configuration. Vous pouvez tester les paramètres et démarrer le service et répéter ce processus pour tester et valider votre service en continu.

Pour en savoir plus sur le Client Test WCF, consultez [WCF (WcfTestClient.exe) de client de test](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>L’accès aux services WCF dans Visual Studio

Visual Studio simplifie la tâche de création des clients WCF, en générant automatiquement un proxy et un point de terminaison pour les services que vous ajoutez à l’aide de la **ajouter une référence de Service** boîte de dialogue. Toutes les informations de configuration nécessaires sont ajoutées à la *app.config* fichier. La plupart du temps, tout ce que vous avez à faire d’instancier le service pour pouvoir le pour utiliser.

Le **ajouter une référence de Service** boîte de dialogue vous permet d’entrer l’adresse pour un service ou de rechercher un service qui est défini dans votre solution. La boîte de dialogue retourne une liste des services et les opérations fournies par ces services. Il vous permet également de définir l’espace de noms par lequel vous ferez référence les services dans le code.

Le **configurer les références de Service** boîte de dialogue vous permet de personnaliser la configuration pour un service. Vous pouvez modifier l’adresse pour un service, spécifiez le niveau d’accès, le comportement asynchrone et les types de contrat de message et configurer la réutilisation du type.

## <a name="how-to-select-a-service-endpoint"></a>Comment : sélectionner un point de terminaison de service

Certains services Windows Communication Foundation (WCF) exposent plusieurs points de terminaison via lequel un client peut communiquer avec le service. Par exemple, un service peut exposer un point de terminaison qui utilise une liaison HTTP et de nom d’utilisateur et de sécurité de mot de passe et un deuxième point de terminaison qui utilise FTP et l’authentification Windows. Le premier point de terminaison peut être utilisé par les applications qui accèdent au service en dehors d’un pare-feu, tandis que la seconde peut être utilisée sur un intranet.

Dans ce cas, vous pouvez spécifier le `endpointConfigurationName` en tant que paramètre au constructeur pour une référence de service.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Pour sélectionner un point de terminaison de service

1.  Ajoutez une référence à un service WCF en double-cliquant sur le nœud du projet dans **l’Explorateur de solutions** et en choisissant **ajouter une référence de service**.

2.  Dans l’éditeur de Code, ajoutez un constructeur pour la référence de service :

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Remplacez *ServiceReference* avec l’espace de noms pour la référence de service et remplacez *Service1Client* avec le nom du service.

3.  Une liste IntelliSense affiche qui inclut les surcharges du constructeur. Sélectionnez le `endpointConfigurationName As String` de surcharge.

4.  Suivant la surcharge, tapez `=` *ConfigurationName*, où *ConfigurationName* est le nom du point de terminaison que vous souhaitez utiliser.

    > [!NOTE]
    > Si vous ne connaissez pas les noms des points de terminaison disponibles, vous les trouverez dans le *app.config* fichier.

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Pour rechercher les points de terminaison disponibles pour un service WCF

1.  Dans **l’Explorateur de solutions**, avec le bouton droit le **app.config** de fichiers pour le projet qui contient la référence de service, puis cliquez sur **Open**. Le fichier apparaît dans l’éditeur de Code.

2.  Recherchez le `<Client>` balise dans le fichier.

3.  Rechercher en dessous de la `<Client>` balise pour une balise qui commence par `<Endpoint>`.

     Si la référence de service fournit plusieurs points de terminaison, il y aura deux ou plusieurs `<Endpoint` balises.

4.  À l’intérieur de la `<EndPoint>` balise, vous trouverez un `name="` *service quelconque* `"` paramètre (où *service quelconque* représente un nom de point de terminaison). C’est le nom du point de terminaison qui peut être passé à la `endpointConfigurationName As String` surcharge d’un constructeur pour une référence de service.

## <a name="how-to-call-a-service-method-asynchronously"></a>Comment : appeler une méthode de service de façon asynchrone

La plupart des méthodes dans les services Windows Communication Foundation (WCF) peut être appelée de manière synchrone ou asynchrone. Appel d’une méthode asynchrone permet à votre application continuer à travailler pendant que la méthode est appelée lorsqu’il fonctionne sur une connexion lente.

Par défaut, lorsqu’une référence de service est ajoutée à un projet, il est configuré pour appeler des méthodes de manière synchrone. Vous pouvez modifier le comportement pour appeler des méthodes de façon asynchrone en modifiant un paramètre dans le **configurer la référence de Service** boîte de dialogue.

> [!NOTE]
> Cette option est définie sur une base par service. Si une méthode pour un service est appelée de façon asynchrone, toutes les méthodes doivent être appelées de façon asynchrone.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Pour appeler une méthode de service de façon asynchrone

1.  Dans **l’Explorateur de solutions**, sélectionnez la référence de service.

2.  Sur le **projet** menu, cliquez sur **configurer la référence de Service**.

3.  Dans le **configurer la référence de Service** boîte de dialogue, sélectionnez le **générer des opérations asynchrones** case à cocher.

## <a name="how-to-bind-data-returned-by-a-service"></a>Comment : lier des données retournées par un service

Vous pouvez lier des données retournées par un service Windows Communication Foundation (WCF) à un contrôle comme vous pouvez lier n’importe quelle autre source de données à un contrôle. Lorsque vous ajoutez une référence à un service WCF, si le service contient des types composites qui retournent des données, ils sont automatiquement ajoutés à la **des Sources de données** fenêtre.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Pour lier un contrôle à un seul champ de données retournée par un service WCF

1.  Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

   La fenêtre **Sources de données** apparaît.

2.  Dans le **des Sources de données** fenêtre, développez le nœud de votre référence de service. Tous les types composites retournés par l’affichage du service.

3.  Développez le nœud d’un type. Les champs de données pour ce type s’affichent.

4.  Sélectionnez un champ et cliquez sur la flèche déroulante pour afficher une liste des contrôles qui sont disponibles pour le type de données.

5.  Cliquez sur le type de contrôle auquel vous souhaitez lier.

6.  Faites glisser le champ vers un formulaire. Le contrôle est ajouté au formulaire, avec un <xref:System.Windows.Forms.BindingSource> composant et un <xref:System.Windows.Forms.BindingNavigator> composant.

7.  Répétez les étapes 4 à 6 pour les autres champs que vous souhaitez lier.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Pour lier un contrôle au type composite retourné par un service WCF

1.  Sur le **données** menu, sélectionnez **afficher les Sources de données**. La fenêtre **Sources de données** apparaît.

2.  Dans le **des Sources de données** fenêtre, développez le nœud de votre référence de service. Tous les types composites retournés par l’affichage du service.

3.  Sélectionnez un nœud pour un type, cliquez sur la flèche déroulante pour afficher une liste des options disponibles.

4.  Cliquez sur **DataGridView** pour afficher les données dans une grille ou **détails** pour afficher les données dans des contrôles individuels.

5.  Faites glisser le nœud vers le formulaire. Les contrôles sont ajoutés au formulaire, avec un <xref:System.Windows.Forms.BindingSource> composant et un <xref:System.Windows.Forms.BindingNavigator> composant.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Comment : configurer un service pour réutiliser les types existants

Lorsqu’une référence de service est ajoutée à un projet, des types définis dans le service sont générés dans le projet local. Dans de nombreux cas, cela crée des types en double lorsqu’un service utilise des types courants de .NET Framework ou lorsque les types sont définis dans une bibliothèque partagée.

Pour éviter ce problème, les types dans les assemblys référencés sont partagés par défaut. Si vous souhaitez désactiver le partage de type d’un ou plusieurs assemblys, vous pouvez effectuer dans le **configurer les références de Service** boîte de dialogue.

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Pour désactiver le partage de type dans un assembly unique

1.  Dans **l’Explorateur de solutions**, sélectionnez la référence de service.

2.  Sur le **projet** menu, cliquez sur **configurer la référence de Service**.

3.  Dans le **configurer les références de Service** boîte de dialogue, sélectionnez **réutiliser les types dans les assemblys référencés spécifiés**.

4.  Sélectionnez la case à cocher pour chaque assembly dans lequel vous souhaitez activer le partage de type. Pour désactiver le partage de type d’un assembly, laissez la case à cocher.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Pour désactiver le partage de type dans tous les assemblys

1.  Dans **l’Explorateur de solutions**, sélectionnez la référence de service.

2.  Sur le **projet** menu, cliquez sur **configurer la référence de Service**.

3.  Dans le **configurer les références de Service** boîte de dialogue, désactivez le **réutiliser les types dans les assemblys référencés** case à cocher.

## <a name="related-topics"></a>Rubriques connexes

| Titre | Description |
| - | - |
| [Procédure pas à pas : création d’un service WPF simple dans Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Fournit une démonstration détaillée de création et utilisation des services WCF dans Visual Studio. |
| [Procédure pas à pas : Création d’un service de données WCF avec WPF et Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Fournit une démonstration pas à pas montrant comment créer et utiliser des Services de données WCF dans Visual Studio. |
| [Utilisation des outils de développement WCF](/dotnet/framework/wcf/using-the-wcf-development-tools) | Explique comment créer et tester les services WCF dans Visual Studio. |
| | [Guide pratique pour ajouter, mettre à jour ou supprimer une référence de service de données WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Dépannage des références de service](../data-tools/troubleshooting-service-references.md) | Présente certaines erreurs courantes qui peuvent se produire avec les références de service et comment les éviter. |
| [Débogage de services WCF](../debugger/debugging-wcf-services.md) | Décrit les problèmes de débogage courants et les techniques que vous pouvez rencontrer lors du débogage de services WCF. |
| [Procédure pas à pas : Création d’une application de données multiniveau](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Fournit des instructions pas à pas pour créer un dataset typé et diviser le code du TableAdapter et du dataset en plusieurs projets. |
| [Configurer la boîte de dialogue Référence de service](../data-tools/configure-service-reference-dialog-box.md) | Décrit les éléments d’interface utilisateur de la **configurer la référence de Service** boîte de dialogue. |

## <a name="reference"></a>Référence

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)