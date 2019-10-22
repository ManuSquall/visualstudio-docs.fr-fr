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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c83e6b85e8657487254f1f4fb275a6280c786ff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72638942"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Services Windows Communication Foundation et services de données WCF dans Visual Studio

Visual Studio fournit des outils pour l’utilisation de Windows Communication Foundation (WCF) et WCF Data Services, des technologies Microsoft pour la création d’applications distribuées. Cette rubrique fournit une introduction aux services du point de vue de Visual Studio. Pour obtenir la documentation complète, consultez [WCF Data Services 4,5](/dotnet/framework/data/wcf/index).

## <a name="what-is-wcf"></a>Qu’est-ce que WCF ?

Windows Communication Foundation (WCF) est une infrastructure unifiée pour la création d’applications distribuées sécurisées, fiables, transactionnelles et interopérables. Il remplace les anciennes technologies de communication interprocessus, telles que les services Web ASMX, .NET Remoting, Enterprise Services (DCOM) et MSMQ. WCF réunit les fonctionnalités de toutes ces technologies dans le cadre d’un modèle de programmation unifié. Cela simplifie l’expérience du développement d’applications distribuées.

### <a name="what-are-wcf-data-services"></a>Que sont les WCF Data Services

WCF Data Services est une implémentation de la norme de protocole OData (Open Data).  WCF Data Services vous permet d’exposer des données tabulaires sous la forme d’un ensemble d’API REST, ce qui vous permet de retourner des données à l’aide de verbes HTTP standard, tels que obtenir, poster, PUT ou DELETE. Côté serveur, WCF Data Services sont remplacés par [API Web ASP.net](http://www.asp.net/web-api) pour la création de nouveaux services OData. La bibliothèque cliente WCF Data Services continue d’être un bon choix pour l’utilisation des services OData dans une application .NET à partir de Visual Studio (**projet**  > **Ajouter une référence de service**). Pour plus d’informations, consultez [WCF Data Services 4.5](http://go.microsoft.com/fwlink/?LinkID=119952).

### <a name="wcf-programming-model"></a>Modèle de programmation WCF

Le modèle de programmation WCF repose sur la communication entre deux entités : un service WCF et un client WCF. Le modèle de programmation est encapsulé dans l’espace de noms <xref:System.ServiceModel> dans .NET.

### <a name="wcf-service"></a>Service WCF

Un service WCF est basé sur une interface qui définit un contrat entre le service et le client. Elle est marquée avec un attribut <xref:System.ServiceModel.ServiceContractAttribute>, comme illustré dans le code suivant :

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

Vous définissez des fonctions ou des méthodes qui sont exposées par un service WCF en les marquant avec un attribut <xref:System.ServiceModel.OperationContractAttribute>.

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

En outre, vous pouvez exposer des données sérialisées en marquant un type composite avec un attribut <xref:System.Runtime.Serialization.DataContractAttribute>. Cela active la liaison de données dans un client.

Une fois qu’une interface et ses méthodes sont définies, elles sont encapsulées dans une classe qui implémente l’interface. Une classe de service WCF unique peut implémenter plusieurs contrats de service.

Un service WCF est exposé à la consommation par le biais de ce qu’on appelle un *point de terminaison*. Le point de terminaison offre le seul moyen de communiquer avec le service. vous ne pouvez pas accéder au service par le biais d’une référence directe, comme vous le feriez avec d’autres classes.

Un point de terminaison se compose d’une adresse, d’une liaison et d’un contrat. L’adresse définit l’emplacement du service ; Il peut s’agir d’une URL, d’une adresse FTP ou d’un chemin d’accès réseau ou local. Une liaison définit la façon dont vous communiquez avec le service. Les liaisons WCF fournissent un modèle polyvalent pour la spécification d’un protocole tel que HTTP ou FTP, un mécanisme de sécurité tel que l’authentification Windows ou des noms d’utilisateur et des mots de passe, et bien plus encore. Un contrat comprend les opérations qui sont exposées par la classe de service WCF.

Plusieurs points de terminaison peuvent être exposés pour un seul service WCF. Cela permet à différents clients de communiquer avec le même service de différentes façons. Par exemple, un service bancaire peut fournir un point de terminaison pour les employés et un autre pour les clients externes, chacun utilisant une adresse, une liaison et/ou un contrat différents.

### <a name="wcf-client"></a>Client WCF (WCF client)

Un client WCF se compose d’un *proxy* qui permet à une application de communiquer avec un service WCF, et d’un point de terminaison qui correspond à un point de terminaison défini pour le service. Le proxy est généré côté client dans le fichier *app. config* et contient des informations sur les types et les méthodes qui sont exposés par le service. Pour les services qui exposent plusieurs points de terminaison, le client peut choisir celui qui correspond le mieux à ses besoins, par exemple, pour communiquer sur HTTP et utiliser l’authentification Windows.

Après la création d’un client WCF, vous référencez le service dans votre code comme vous le feriez pour tout autre objet. Par exemple, pour appeler la méthode `GetData` présentée précédemment, vous écrivez du code qui ressemble à ce qui suit :

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Outils WCF dans Visual Studio

Visual Studio fournit des outils pour vous aider à créer des services WCF et des clients WCF. Pour obtenir une procédure pas à pas qui illustre les outils, consultez [procédure pas à pas : création d’un service WCF simple dans Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).

### <a name="create-and-test-wcf-services"></a>Créer et tester des services WCF

Vous pouvez utiliser les modèles Visual Studio WCF comme base pour créer rapidement votre propre service. Vous pouvez ensuite utiliser l’hôte auto du service WCF et le client test WCF pour déboguer et tester le service. Ces outils offrent un cycle de débogage et de test rapide et pratique, et éliminent la nécessité de valider un modèle d’hébergement à un moment précoce.

#### <a name="wcf-templates"></a>Modèles WCF

Les modèles Visual Studio WCF fournissent une structure de classe de base pour le développement de services. Plusieurs modèles WCF sont disponibles dans la boîte de dialogue **Ajouter un nouveau projet** . Il s’agit notamment des projets lLibrary service WCF, des sites Web de service WCF et des modèles d’élément de service WCF.

Lorsque vous sélectionnez un modèle, des fichiers sont ajoutés pour un contrat de service, une implémentation de service et une configuration de service. Tous les attributs nécessaires sont déjà ajoutés, créant un type de service « Hello World » simple et vous n’avez pas eu à écrire de code. Bien sûr, vous souhaiterez ajouter du code pour fournir des fonctions et des méthodes pour votre service réel, mais les modèles fournissent la Fondation de base.

Pour en savoir plus sur les modèles WCF, consultez [modèles Visual Studio WCF](/dotnet/framework/wcf/wcf-vs-templates).

#### <a name="wcf-service-host"></a>Hôte de service WCF

Quand vous démarrez le débogueur Visual Studio (en appuyant sur **F5**) pour un projet de service WCF, l’outil hôte de service WCF est démarré automatiquement pour héberger le service localement. L’hôte de service WCF énumère les services dans un projet de service WCF, charge la configuration du projet et instancie un hôte pour chaque service qu’il trouve.

À l’aide de l’hôte de service WCF, vous pouvez tester un service WCF sans écrire de code supplémentaire ni valider un hôte spécifique pendant le développement.

Pour en savoir plus sur l’hôte de service WCF, consultez [hôte de service WCF (WcfSvcHost. exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe).

#### <a name="wcf-test-client"></a>Client test WCF

L’outil client test WCF vous permet d’entrer des paramètres de test, de soumettre cette entrée à un service WCF et d’afficher la réponse renvoyée par le service. Il fournit une expérience de test de service pratique lorsque vous l’associez à l’hôte de service WCF. Recherchez l’outil dans le dossier *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE* .

Quand vous appuyez sur **F5** pour déboguer un projet de service WCF, le client test WCF s’ouvre et affiche une liste des points de terminaison de service définis dans le fichier de configuration. Vous pouvez tester les paramètres et démarrer le service, puis répéter ce processus pour tester et valider en continu votre service.

Pour en savoir plus sur le client test WCF, consultez [client test WCF (WcfTestClient. exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe).

### <a name="accessing-wcf-services-in-visual-studio"></a>Accès aux services WCF dans Visual Studio

Visual Studio simplifie la tâche de création de clients WCF, en générant automatiquement un proxy et un point de terminaison pour les services que vous ajoutez à l’aide de la boîte de dialogue **Ajouter une référence de service** . Toutes les informations de configuration nécessaires sont ajoutées au fichier *app. config* . La plupart du temps, il vous suffit d’instancier le service pour pouvoir l’utiliser.

La boîte de dialogue **Ajouter une référence de service** vous permet d’entrer l’adresse d’un service ou de rechercher un service défini dans votre solution. La boîte de dialogue retourne une liste de services et les opérations fournies par ces services. Elle vous permet également de définir l’espace de noms par lequel vous allez référencer les services dans le code.

La boîte de dialogue **configurer les références de service** vous permet de personnaliser la configuration d’un service. Vous pouvez modifier l’adresse d’un service, spécifier un niveau d’accès, un comportement asynchrone et des types de contrat de message, et configurer la réutilisation de type.

## <a name="how-to-select-a-service-endpoint"></a>Comment : sélectionner un point de terminaison de service

Certains services de Windows Communication Foundation (WCF) exposent plusieurs points de terminaison par le biais desquels un client peut communiquer avec le service. Par exemple, un service peut exposer un point de terminaison qui utilise une liaison HTTP et une sécurité de nom d’utilisateur et de mot de passe, ainsi qu’un deuxième point de terminaison qui utilise l’authentification FTP et Windows. Le premier point de terminaison peut être utilisé par les applications qui accèdent au service à partir de l’extérieur d’un pare-feu, tandis que le second peut être utilisé sur un intranet.

Dans ce cas, vous pouvez spécifier le `endpointConfigurationName` en tant que paramètre du constructeur pour une référence de service.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>Pour sélectionner un point de terminaison de service

1. Ajoutez une référence à un service WCF en cliquant avec le bouton droit sur le nœud du projet dans **Explorateur de solutions** et en choisissant **Ajouter une référence de service**.

2. Dans l’éditeur de code, ajoutez un constructeur pour la référence de service :

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > Remplacez *ServiceReference* par l’espace de noms de la référence de service et remplacez *Service1Client* par le nom du service.

3. Une liste IntelliSense s’affiche, qui comprend les surcharges du constructeur. Sélectionnez la surcharge `endpointConfigurationName As String`.

4. Après la surcharge, tapez `=` *ConfigurationName*, où *ConfigurationName* est le nom du point de terminaison que vous souhaitez utiliser.

    > [!NOTE]
    > Si vous ne connaissez pas les noms des points de terminaison disponibles, vous pouvez les trouver dans le fichier *app. config* .

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>Pour rechercher les points de terminaison disponibles pour un service WCF

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier **app. config** du projet qui contient la référence de service, puis cliquez sur **ouvrir**. Le fichier s’affiche dans l’éditeur de code.

2. Recherchez la balise `<Client>` dans le fichier.

3. Recherchez, sous la balise `<Client>`, une balise qui commence par `<Endpoint>`.

     Si la référence de service fournit plusieurs points de terminaison, il y aura au moins deux balises `<Endpoint`.

4. À l’intérieur de la balise `<EndPoint>`, vous trouverez un paramètre `name="`*SomeService* `"` (où *SomeService* représente un nom de point de terminaison). Il s’agit du nom du point de terminaison qui peut être passé à la surcharge `endpointConfigurationName As String` d’un constructeur pour une référence de service.

## <a name="how-to-call-a-service-method-asynchronously"></a>Comment : appeler une méthode de service de façon asynchrone

La plupart des méthodes des services Windows Communication Foundation (WCF) peuvent être appelées de façon synchrone ou asynchrone. L’appel d’une méthode de manière asynchrone permet à votre application de continuer à fonctionner pendant l’appel de la méthode lorsqu’elle fonctionne sur une connexion lente.

Par défaut, lorsqu’une référence de service est ajoutée à un projet, elle est configurée pour appeler des méthodes de manière synchrone. Vous pouvez modifier le comportement pour appeler des méthodes de façon asynchrone en modifiant un paramètre dans la boîte de dialogue **configurer la référence de service** .

> [!NOTE]
> Cette option est définie sur une base par service. Si une méthode pour un service est appelée de manière asynchrone, toutes les méthodes doivent être appelées de façon asynchrone.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>Pour appeler une méthode de service de façon asynchrone

1. Dans **Explorateur de solutions**, sélectionnez la référence de service.

2. Dans le menu **projet** , cliquez sur **configurer la référence de service**.

3. Dans la boîte de dialogue **configurer la référence de service** , activez la case à cocher générer des **opérations asynchrones** .

## <a name="how-to-bind-data-returned-by-a-service"></a>Comment : lier des données retournées par un service

Vous pouvez lier des données retournées par un service Windows Communication Foundation (WCF) à un contrôle, tout comme vous pouvez lier n’importe quelle autre source de données à un contrôle. Lorsque vous ajoutez une référence à un service WCF, si le service contient des types composites qui retournent des données, ils sont automatiquement ajoutés à la fenêtre **sources de données** .

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>Pour lier un contrôle à un champ de données unique retourné par un service WCF

1. Dans le menu **Données** , cliquez sur **Afficher les sources de données**.

   La fenêtre **Sources de données** apparaît.

2. Dans la fenêtre **sources de données** , développez le nœud de votre référence de service. Tous les types composites retournés par le service sont affichés.

3. Développez un nœud pour un type. Les champs de données de ce type apparaissent.

4. Sélectionnez un champ et cliquez sur la flèche déroulante pour afficher la liste des contrôles disponibles pour le type de données.

5. Cliquez sur le type de contrôle que vous souhaitez lier.

6. Faites glisser le champ sur un formulaire. Le contrôle est ajouté au formulaire, avec un composant <xref:System.Windows.Forms.BindingSource> et un composant <xref:System.Windows.Forms.BindingNavigator>.

7. Répétez les étapes 4 à 6 pour tous les autres champs que vous souhaitez lier.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>Pour lier un contrôle à un type composite retourné par un service WCF

1. Dans le menu **données** , sélectionnez **afficher les sources de données**. La fenêtre **Sources de données** apparaît.

2. Dans la fenêtre **sources de données** , développez le nœud de votre référence de service. Tous les types composites retournés par le service sont affichés.

3. Sélectionnez un nœud pour un type, puis cliquez sur la flèche déroulante pour afficher la liste des options disponibles.

4. Cliquez sur **DataGridView** pour afficher les données dans une grille ou sur les **Détails** pour afficher les données dans des contrôles individuels.

5. Faites glisser le nœud sur le formulaire. Les contrôles sont ajoutés au formulaire, avec un composant <xref:System.Windows.Forms.BindingSource> et un composant <xref:System.Windows.Forms.BindingNavigator>.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>Comment : configurer un service pour réutiliser les types existants

Lorsqu’une référence de service est ajoutée à un projet, tous les types définis dans le service sont générés dans le projet local. Dans de nombreux cas, cela crée des types dupliqués lorsqu’un service utilise des types .NET courants ou lorsque des types sont définis dans une bibliothèque partagée.

Pour éviter ce problème, les types des assemblys référencés sont partagés par défaut. Si vous souhaitez désactiver le partage de type pour un ou plusieurs assemblys, vous pouvez le faire dans la boîte de dialogue **configurer les références de service** .

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>Pour désactiver le partage de type dans un assembly unique

1. Dans **Explorateur de solutions**, sélectionnez la référence de service.

2. Dans le menu **projet** , cliquez sur **configurer la référence de service**.

3. Dans la boîte de dialogue **configurer les références de service** , sélectionnez **réutiliser les types dans les assemblys référencés spécifiés**.

4. Activez la case à cocher pour chaque assembly dans lequel vous souhaitez activer le partage de type. Pour désactiver le partage de type pour un assembly, laissez la case à cocher désactivée.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>Pour désactiver le partage de type dans tous les assemblys

1. Dans **Explorateur de solutions**, sélectionnez la référence de service.

2. Dans le menu **projet** , cliquez sur **configurer la référence de service**.

3. Dans la boîte de dialogue **configurer les références de service** , désactivez la case à cocher **réutiliser les types dans les assemblys référencés** .

## <a name="related-topics"></a>Rubriques connexes

| Titre | Description |
| - | - |
| [Procédure pas à pas : création d’un service WPF simple dans Windows Forms](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Fournit une démonstration pas à pas de la création et de l’utilisation des services WCF dans Visual Studio. |
| [Procédure pas à pas : Création d’un service de données WCF avec WPF et Entity Framework](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Fournit une démonstration pas à pas de la création et de l’utilisation de WCF Data Services dans Visual Studio. |
| [Utilisation des outils de développement WCF](/dotnet/framework/wcf/using-the-wcf-development-tools) | Explique comment créer et tester des services WCF dans Visual Studio. |
| | [Guide pratique pour ajouter, mettre à jour ou supprimer une référence de service de données WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [Dépannage des références de service](../data-tools/troubleshooting-service-references.md) | Présente des erreurs courantes qui peuvent se produire avec les références de service et comment les empêcher. |
| [Débogage de services WCF](../debugger/debugging-wcf-services.md) | Décrit les problèmes de débogage courants et les techniques que vous pouvez rencontrer lors du débogage de services WCF. |
| [Procédure pas à pas : Création d’une application de données multiniveau](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | Fournit des instructions pas à pas pour créer un dataset typé et diviser le code du TableAdapter et du dataset en plusieurs projets. |
| [Configurer la boîte de dialogue Référence de service](../data-tools/configure-service-reference-dialog-box.md) | Décrit les éléments de l’interface utilisateur de la boîte de dialogue **configurer la référence de service** . |

## <a name="reference"></a>Reference

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>Voir aussi

- [Outils de données Visual Studio pour .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)