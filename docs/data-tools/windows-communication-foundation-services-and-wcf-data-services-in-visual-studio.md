---
title: "Windows Communication Foundation Services and WCF Data Services in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services, WCF Data"
  - "WCF services, binding to"
  - "WCF services, asynchronous service methods"
  - "service references [Visual Studio]"
  - "WCF Data Services"
  - "asynchronous calls"
  - "service references [Visual Studio], type sharing"
  - "endpoints [WCF]"
  - "asynchronous service methods"
  - "service references [Visual Studio] endpoints"
  - "WCF services, type sharing"
  - "Windows Communication Foundation, in Visual Studio"
  - "services, WCF"
  - "WCF service, Visual Studio"
  - "data services, WCF"
  - "services, in Visual Studio"
  - "data binding [Visual Studio], WCF"
  - "service endpoints [Visual Studio]"
  - "service references [Visual Studio], asynchronous calls"
  - "services, Windows Communication Foundation"
  - "type sharing in WCF services"
  - "WCF services, endpoints"
  - "service method, called asynchronously[Visual Studio]"
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 26
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Communication Foundation Services and WCF Data Services in Visual Studio
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 fournit des outils pour l'utilisation de Windows Communication Foundation \(WCF\) et d'[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], des technologies Microsoft pour la création d'applications distribuées.  Cette rubrique fournit une introduction aux services du point de vue de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Qu'est\-ce que WCF ?  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] est une infrastructure unifiée de création d'applications distribuées interopérables sécurisées, fiables et traitées.  Dans les versions antérieures de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], plusieurs technologies pouvaient être utilisées pour communiquer entre les applications.  
  
 Pour partager les informations de manière à les rendre accessibles à partir de n'importe quelle plateforme, vous utiliserez un service Web \(également appelé service Web ASMX\).  Pour déplacer uniquement les données exécutées sur le système d'exploitation Windows entre un client et un serveur, vous utiliserez .NET Remoting.  Pour obtenir des communications traitées, vous utiliserez Enterprise Services \(DCOM\) ou, pour obtenir un modèle de file d'attente, vous utiliserez Message Queuing \(également appelé MSMQ\).  
  
 WCF réunit les fonctionnalités de toutes ces technologies dans un modèle de programmation unifié.  Cela simplifie le développement des applications distribuées.  
  
#### Que sont les services de données WCF ?  
 Les services d'[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] interagissent directement avec une base de données, ce qui vous permet de retourner des données à l'aide de verbes HTTP standard tels que GET, POST, PUT ou DELETE.  En général, [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] constitue un bon choix pour les applications utilisées pour créer, mettre à jour ou supprimer des enregistrements dans une base de données.  Pour plus d'informations, consultez [ADO.NET Data Services Framework](http://go.microsoft.com/fwlink/?LinkID=119952).  
  
### Modèle de programmation WCF  
 Le modèle de programmation WCF est basé sur la communication entre deux entités : un service WCF et un client WCF.  Le modèle de programmation est encapsulé dans l'espace de noms <xref:System.ServiceModel> dans le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### Service WCF  
 Un service WCF est basé sur une interface qui définit un contrat entre le service et le client.  Il est marqué avec un attribut <xref:System.ServiceModel.ServiceContractAttribute>, comme illustré dans le code suivant :  
  
 [!code-cs[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-cs[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 Vous définissez les fonctions ou les méthodes exposées par un service WCF en les marquant avec un attribut <xref:System.ServiceModel.OperationContractAttribute>.  En outre, vous pouvez exposer les données sérialisées en marquant un type composite avec un attribut <xref:System.Runtime.Serialization.DataContractAttribute>.  Cela active la liaison de données dans un client.  
  
 Une fois l'interface et ses méthodes définies, elles sont encapsulées dans une classe qui implémente l'interface.  Une seule classe de service WCF peut implémenter plusieurs contrats de service.  
  
 Un service WCF est utilisé via ce que l'on appelle un *point de terminaison*.  Le point de terminaison fournit le seul moyen de communication avec le service ; vous ne pouvez pas accéder au service via une référence directe comme avec les autres classes.  
  
 Un point de terminaison se compose d'une adresse, d'une liaison et d'un contrat.  L'adresse définit l'emplacement du service ; cela peut être une URL, une adresse FTP ou un chemin d'accès réseau ou local.  Une liaison définit la façon dont vous communiquez avec le service.  Les liaisons WCF fournissent un modèle polyvalent pour spécifier un protocole tel qu'HTTP ou FTP, un mécanisme de sécurité tel que l'authentification Windows ou des noms d'utilisateurs et des mots de passe, etc.  Un contrat inclut les opérations exposées par la classe de service WCF.  
  
 Plusieurs points de terminaison peuvent être exposés pour un seul service WCF.  Cela permet aux différents clients de communiquer avec le même service de plusieurs façons.  Par exemple, un service bancaire peut fournir un point de terminaison pour les employés et un autre point pour les clients externes, chacun utilisant une adresse, une liaison et\/ou un contrat différents.  
  
#### Client WCF  
 Un client WCF se compose d'un *proxy* qui permet à une application de communiquer avec un service WCF et d'un point de terminaison qui correspond à un point de terminaison défini pour le service.  Le proxy est généré côté client dans le fichier app.config et inclut des informations sur les types et les méthodes exposés par le service.  Pour les services qui exposent plusieurs points de terminaison, le client peut sélectionner celui qui correspond le mieux à ses besoins, par exemple, pour communiquer sur HTTP et utiliser l'authentification Windows.  
  
 Après avoir créé un client WCF, vous référencez le service dans votre code comme vous le feriez pour n'importe quel autre objet.  Par exemple, pour appeler la méthode `GetData` présentée précédemment, écrivez un code similaire au code suivant :  
  
 [!code-cs[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## Outils WCF dans Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 fournit des outils pour vous aider à créer des services WCF et des clients WCF.  Pour obtenir une procédure pas à pas illustrant les outils, consultez [Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).  
  
### Création et test de services WCF  
 Vous pouvez utiliser les modèles [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] WCF comme base pour créer rapidement votre propre service.  Vous pouvez ensuite utiliser l'hôte de service WCF et le client test WCF pour déboguer et tester le service.  Ces outils fournissent ensemble un cycle de test et de débogage rapide et pratique et éliminent la nécessité de valider un modèle d'hébergement lors d'une phase préliminaire.  
  
#### Modèles WCF  
 Les modèles [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] WCF fournissent une structure de classe de base pour le développement du service.  Plusieurs modèles WCF sont disponibles dans la boîte de dialogue **Ajouter un nouveau projet**.  Ceux\-ci incluent des modèles de projet de la Bibliothèque de services WCF, de sites Web de service WCF et d'éléments de service WCF.  
  
 Lorsque vous sélectionnez un modèle, les fichiers sont ajoutés pour un contrat de service, une implémentation de service et une configuration de service.  Tous les attributs nécessaires sont déjà ajoutés, ce qui crée un type de service simple « Hello World », sans avoir à écrire de code.  Vous souhaiterez évidemment ajouter du code pour fournir des fonctions et des méthodes pour votre service réaliste, mais les modèles fournissent la fondation de base.  
  
 Pour plus d'informations sur les modèles WCF, consultez [Modèles Visual Studio WCF](../Topic/WCF%20Visual%20Studio%20Templates.md).  
  
#### Hôte de service WCF  
 Lorsque vous démarrez le débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(en appuyant sur F5\) pour un projet de service WCF, l'outil Hôte de service WCF est démarré automatiquement pour héberger le service localement.  L'hôte de service WCF énumère les services dans un projet de service WCF, charge la configuration du projet et instancie un hôte pour chaque service trouvé.  
  
 À l'aide de l'hôte de service WCF, vous pouvez tester un service WCF sans écrire de code supplémentaire ou valider un hôte spécifique au cours du développement.  
  
 Pour plus d'informations sur l'hôte de service WCF, consultez [Hôte de service WCF \(WcfSvcHost.exe\)](../Topic/WCF%20Service%20Host%20\(WcfSvcHost.exe\).md).  
  
#### Client test WCF  
 L'outil Client test WCF vous permet d'entrer des paramètres de test, de soumettre cette entrée à un service WCF et de consulter la réponse renvoyée par le service.  Il fournit une expérience de test de service pratique lorsque vous le combinez avec l'hôte de service WCF.  
  
 Lorsque vous appuyez sur F5 pour déboguer un projet de service WCF, le client test WCF s'ouvre et affiche la liste des points de terminaison de service définis dans le fichier de configuration.  Vous pouvez tester les paramètres et démarrer le service, et répéter ce processus pour tester et valider en continu votre service.  
  
 Pour plus d'informations sur le client test WCF, consultez [Client test WCF \(WcfTestClient.exe\)](../Topic/WCF%20Test%20Client%20\(WcfTestClient.exe\).md).  
  
### Accès aux services WCF dans Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] simplifie la tâche de création des clients WCF, en générant automatiquement un proxy et un point de terminaison pour les services que vous ajoutez à l'aide de la boîte de dialogue d' **Ajouter une référence de service** .  Toutes les informations de configuration nécessaires sont ajoutées au fichier app.config. Le plus souvent, tout ce que vous avez à faire consiste à instancier le service pour l'utiliser.  
  
 La boîte de dialogue **Ajouter une référence de service** vous permet d'entrer l'adresse pour un service ou de rechercher un service défini dans votre solution.  La boîte de dialogue retourne une liste de services et les opérations fournies par ces services.  Elle vous permet également de définir l'espace de noms de référence des services dans le code.  
  
 La boîte de dialogue **Configurer les références de service** vous permet de personnaliser la configuration pour un service.  Vous pouvez modifier l'adresse pour un service, spécifier le niveau d'accès, le comportement asynchrone et les types de contrats de message, et configurer la réutilisation du type.  
  
## Comment : sélectionnez un point de terminaison de service  
 Certains services Windows Communication Foundation \(WCF\) exposent plusieurs points de terminaison auxquels un client peut communiquer avec le service.  Par exemple, un service peut exposer un point de terminaison qui utilise une liaison HTTP et nom d'utilisateur\/sécurité par mot de passe et un deuxième point de terminaison qui utilise FTP et l'authentification Windows.  Le premier point de terminaison peut être utilisé par les applications qui accèdent au service en dehors d'un pare\-feu, alors que la seconde peut être utilisée sur un intranet.  
  
 Dans ce cas, vous pouvez spécifier le `endpointConfigurationName` comme paramètre du constructeur d'une référence de service.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Pour sélectionner un point de terminaison de service  
  
1.  Ajoutez une référence à un service WCF.  Pour plus d'informations, consultez [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md).  
  
2.  Dans l'éditeur de code, ajoutez un constructeur pour la référence de service :  
  
    ```vb#  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```c#  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  Remplacez *ServiceReference* par l'espace de noms pour la référence de service et remplacez *Service1Client* par le nom du service.  
  
3.  Une liste IntelliSense contenant les surcharges pour le constructeur s'affiche.  Sélectionnez la surcharge `endpointConfigurationName As String`.  
  
4.  Suivant la surcharge, tapez `=` *Nom de configuration*, où *Nom de configuration* est le nom du point de terminaison à utiliser.  
  
    > [!NOTE]
    >  Si vous ne connaissez pas les noms des points de terminaison disponibles, vous pouvez les rechercher dans le fichier app.config.  
  
#### Pour rechercher les points de terminaison disponibles pour un service WCF  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier app.config pour le projet qui contient la référence de service puis cliquez sur **Ouvrir**.  Le fichier s'ouvre dans l'éditeur de code.  
  
2.  Recherchez la balise `<Client>` dans le fichier.  
  
3.  Recherchez une balise qui démarre avec `<Endpoint>` sous la balise `<Client>`.  
  
     Si la référence de service fournit plusieurs points de terminaison, il y aura au moins deux de balises `<Endpoint`.  
  
4.  Dans la balise `<EndPoint>`, vous trouverez un paramètre `name="`*Service quelconque*`"` \(où *Service quelconque* représente un nom de point de terminaison\).  Il s'agit du nom du point de terminaison qui peut être passé à la surcharge `endpointConfigurationName As String` d'un constructeur d'une référence de service.  
  
## Comment : appelez une méthode de service de façon asynchrone  
 La plupart des méthodes dans les services Windows Communication Foundation \(WCF\) peuvent être appelées de façon synchrone ou de façon asynchrone.  Lorsqu'une méthode est appelée de façon asynchrone, votre application peut continuer à fonctionner pendant que la méthode est appelée lors d'une connexion lente.  
  
 Par défaut, lorsqu'une référence de service est ajoutée à un projet, elle est configurée pour appeler des méthodes de façon synchrone.  Pour changer ce comportement et appeler de façon asynchrone des méthodes, vous devez modifier un paramètre dans la boîte de dialogue **Configurer la référence de service**.  
  
> [!NOTE]
>  Cette option est définie service par service.  Si une méthode est appelée de façon asynchrone pour un service, toutes les méthodes doivent être appelées de façon asynchrone.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Pour appeler une méthode de service de manière asynchrone  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez la référence de service.  
  
2.  Dans le menu **Projet**, cliquez sur **Configurer la référence de service**.  
  
3.  Dans la boîte de dialogue **Configurer la référence de service**, activez la case à cocher **Générer des opérations asynchrones**.  
  
## Comment : Données de liaison retournées par un service  
 Vous pouvez lier des données retournées par un service Windows Communication Foundation \(WCF\) à un contrôle, de même que vous pouvez lier toute autre source de données à un contrôle.  Lorsque vous ajoutez une référence à un service WCF, si le service contient des types composites qui retournent des données, ils sont alors automatiquement ajoutés à la fenêtre **Sources de données**.  
  
#### Pour lier un contrôle à un seul champ de données retourné par un service WCF  
  
1.  Dans le menu **Données**, cliquez sur **Afficher les sources de données**.  La fenêtre **Sources de données** s'affiche.  
  
2.  Dans la fenêtre **Sources de données**, développez le nœud de votre référence de service.  Tous les types composites retournés par le service s'affichent.  
  
3.  Développez le nœud d'un type.  Les champs de données de ce type s'affichent.  
  
4.  Sélectionnez un champ et cliquez sur la flèche de déroulement pour afficher la liste des contrôles qui sont disponibles pour ce type de données.  
  
5.  Cliquez sur le type de contrôle avec lequel vous souhaitez établir une liaison.  
  
6.  Faites glisser le champ sur un formulaire.  Le contrôle est ajouté au formulaire avec un composant <xref:System.Windows.Forms.BindingSource> et un composant <xref:System.Windows.Forms.BindingNavigator>.  
  
7.  Répétez les étapes 4 à 6 pour tous les autres champs que vous souhaitez lier.  
  
#### Pour lier un contrôle au type composite retourné par un service WCF  
  
1.  Dans le menu **Données**, sélectionnez **Afficher les sources de données**.  La fenêtre **Sources de données** s'affiche.  
  
2.  Dans la fenêtre **Sources de données**, développez le nœud de votre référence de service.  Tous les types composites retournés par le service s'affichent.  
  
3.  Sélectionnez le nœud d'un type et cliquez sur la flèche de déroulement pour afficher la liste des options disponibles.  
  
4.  Cliquez sur **DataGridView** pour afficher les données dans une grille ou sur **Détails** pour afficher les données dans des contrôles individuels.  
  
5.  Faites glisser le nœud sur le formulaire.  Les contrôles sont ajoutés au formulaire avec un composant <xref:System.Windows.Forms.BindingSource> et un composant <xref:System.Windows.Forms.BindingNavigator>.  
  
## Comment : Configurez un service de réutiliser des types existants  
 Lorsqu'une référence de service est ajoutée à un projet, tous les types définis dans le service sont générés dans le projet local.  Dans de nombreux cas, cela crée des types en double lorsqu'un service utilise des types [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] communs ou lorsque les types sont définis dans une bibliothèque partagée.  
  
 Pour éviter ce problème, les types qui figurent dans les assemblys référencés sont partagés par défaut.  Pour désactiver le partage de type d'un ou de plusieurs assemblys, vous pouvez utiliser la boîte de dialogue **Configurer les références de service**.  
  
#### Pour désactiver le partage de type dans un seul assembly  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez la référence de service.  
  
2.  Dans le menu **Projet**, cliquez sur **Configurer la référence de service**.  
  
3.  Dans la boîte de dialogue **Configurer les références de service**, activez la case à cocher **Réutiliser les types dans les assemblys référencés spécifiés**.  
  
4.  Activez la case à cocher de chaque assembly dans lequel vous souhaitez activer le partage de type.  Pour désactiver le partage de type d'un assembly, n'activez pas cette case à cocher.  
  
#### Pour désactiver le partage de type dans tous les assemblys  
  
1.  Dans l'**Explorateur de solutions**, sélectionnez la référence de service.  
  
2.  Dans le menu **Projet**, cliquez sur **Configurer la référence de service**.  
  
3.  Dans la boîte de dialogue **Configurer les références de service**, désactivez la case à cocher **Réutiliser les types dans les assemblys référencés spécifiés**.  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Fournit une démonstration pas à pas de la création et de l'utilisation de services WCF dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Fournit une démonstration pas à pas de la création et de l'utilisation d'[!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Utilisation des outils de développement WCF](../Topic/Using%20the%20WCF%20Development%20Tools.md)|Explique comment créer et tester des services WCF dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)|Décrit comment ajouter, mettre à jour ou supprimer des services WCF d'un projet.|  
|[How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Explique comment référencer et utiliser [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)|Décrit comment ajouter une référence à un service Web XML \(ASMX\) dans un projet.|  
|[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)|Présente certaines erreurs courantes qui peuvent se produire avec les références de service et la façon de les éviter.|  
|[Débogage de services WCF](../debugger/debugging-wcf-services.md)|Décrit les problèmes et les techniques de débogage courants que vous pouvez rencontrer lors du débogage de services WCF.|  
|[Windows Communication Foundation Authentication Service Overview](../Topic/Windows%20Communication%20Foundation%20Authentication%20Service%20Overview.md)|Décrit l'utilisation de WCF pour fournir un service de rôle pour un site Web.|  
|[Messaging in the .NET Compact Framework](http://msdn.microsoft.com/fr-fr/fb74d82c-f81e-46f9-aceb-f875c5c6be4f)|Décrit la prise en charge de la couche de messagerie WCF du .NET Compact Framework.|  
|[Procédure pas à pas : création d'une application de données multicouche](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Fournit des instructions détaillées sur la création d'un groupe de données typé et la séparation du code du TableAdapter et du code du groupe de données en plusieurs projets.|  
|[Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)|Décrit les éléments de l'interface utilisateur de la boîte de dialogue **Ajouter une référence de service**.|  
|[Configurer la référence de service, boîte de dialogue](../data-tools/configure-service-reference-dialog-box.md)|Décrit les éléments de l'interface utilisateur de la boîte de dialogue **Configurer la référence de service**.|  
  
## Référence  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>