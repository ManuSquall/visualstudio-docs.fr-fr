---
title: "Fourniture d&#39;informations de cr&#233;ation de packages et de d&#233;ploiement dans des &#233;l&#233;ments de projet"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.SafeControlEntries"
  - "VS.SharePointTools.Project.ProjectOutputReference"
  - "VS.SharePointTools.Project.FeatureProperties"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "propriétés de fonctionnalité (développement SharePoint dans Visual Studio)"
  - "récepteur de fonctionnalité (développement SharePoint dans Visual Studio)"
  - "références de sortie de projet (développement SharePoint dans Visual Studio)"
  - "contrôles sécurisés (développement SharePoint dans Visual Studio)"
  - "développement SharePoint dans Visual Studio, outils d'empaquetage avancés"
  - "développement SharePoint dans Visual Studio, propriétés de fonctionnalité"
  - "développement SharePoint dans Visual Studio, récepteur de fonctionnalité"
  - "développement SharePoint dans Visual Studio, références de sortie de projet"
  - "développement SharePoint dans Visual Studio, contrôles sécurisés"
ms.assetid: 209ff3b9-d701-4d27-9d24-005fcc811cbe
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Fourniture d&#39;informations de cr&#233;ation de packages et de d&#233;ploiement dans des &#233;l&#233;ments de projet
  Tous les éléments de projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ont des propriétés que vous pouvez utiliser pour fournir des données supplémentaires lorsque le projet est déployé sur SharePoint.  Ces propriétés sont les suivantes :  
  
-   Propriétés de la fonctionnalité  
  
-   Récepteurs de fonctionnalité  
  
-   Références de sortie de projet  
  
-   Entrées de contrôle sécurisé  
  
 Ces propriétés s'affichent dans la fenêtre **Propriétés**.  
  
## Propriétés de la fonctionnalité  
 Utilisez la propriété **Feature Properties** pour spécifier des données que la fonctionnalité utilise.  Les données de propriétés de la fonctionnalité sont un jeu de valeurs \(stocké sous forme de paires clé\/valeur\) inclus avec une fonctionnalité lors du déploiement sur SharePoint.  Après avoir déployé la fonctionnalité, vous pouvez accéder aux valeurs de propriété dans votre code.  
  
 Lorsque vous ajoutez une valeur de propriété de fonctionnalité à un élément de projet, la valeur est ajoutée comme un élément dans le manifeste de la fonctionnalité de l'élément.  Dans un projet de modèle BDC \(Business Data Connectivity\), par exemple, la propriété de fonctionnalité ModelFileName apparaît comme suit :  
  
```  
<Property Key="ModelFileName" Value="BdcModel1\BdcModel1.bdcm" />   
```  
  
 Une fois que vous avez défini une valeur de propriété de fonctionnalité, elle est ajoutée comme élément FeatureProperty dans le fichier .spdata du projet.  Pour plus d'informations sur l'accès aux propriétés dans SharePoint, consultez [SPFeaturePropertyCollection, classe](http://go.microsoft.com/fwlink/?LinkId=177391).  
  
 Les valeurs de propriété de fonctionnalité identiques de tous les éléments de projet sont fusionnées dans le manifeste de fonctionnalité.  Toutefois, si deux éléments de projet différents spécifient la même clé de propriété de fonctionnalité sans que les valeurs correspondent, une erreur de validation se produit.  
  
 Pour ajouter directement des propriétés de fonctionnalité au fichier de fonctionnalités \(\* .feature\), appelez la méthode de modèle d'objet [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint <xref:Microsoft.VisualStudio.SharePoint.Features.IPropertyCollection.Add%2A>.  Si vous utilisez cette méthode, sachez que la même règle à propos de l'ajout de valeurs de propriété de fonctionnalité identiques dans Propriétés de la fonctionnalité s'applique également aux propriétés ajoutées directement au fichier de fonctionnalités.  
  
## Récepteur de fonctionnalité  
 Les récepteurs de fonctionnalité correspondent à du code qui s'exécute lorsque certains événements se produisent pour la fonctionnalité conteneur d'un élément de projet.  Par exemple, vous pouvez définir des récepteurs de fonctionnalité qui s'exécutent lorsque la fonctionnalité est installée, activée ou mise à niveau.  Une manière d'ajouter un récepteur de fonctionnalité consiste à l'ajouter directement à une fonctionnalité, comme décrit dans [Procédure pas à pas : ajout de récepteurs d'événements de fonctionnalité](../sharepoint/walkthrough-add-feature-event-receivers.md).  Une autre manière consiste à référencer un assembly et un nom de classe de récepteur de fonctionnalité dans la propriété **Feature Receiver**.  
  
### Méthode directe  
 Lorsque vous ajoutez directement un récepteur de fonctionnalité à une fonctionnalité, un fichier de code est placé sous le nœud **Fonctionnalité** dans l'Explorateur de solutions.  Lorsque vous générez votre solution SharePoint, le code effectue la compilation dans un assembly et est déployé vers SharePoint.  Par défaut, les propriétés de fonctionnalité **Assembly du récepteur** et **Classe du récepteur** référencent le nom de classe et l'assembly.  
  
### Méthode de référence  
 Une autre manière d'ajouter un récepteur de fonctionnalité consiste à utiliser la propriété **Feature Receiver** d'un élément de projet pour référencer un assembly de récepteur de fonctionnalité.  La valeur de la propriété Feature Receiver a deux sous\-propriétés : **Assembly** et **Class Name**.  L'assembly doit utiliser son nom qualifié complet « fort » et le nom de classe doit être le nom de type complet.  Pour plus d'informations, consultez [Assemblées de nom fort](http://go.microsoft.com/fwlink/?LinkID=169573).  Après avoir déployé la solution vers SharePoint, la fonctionnalité utilise le récepteur de fonctionnalité référencé pour gérer les événements de fonctionnalité.  
  
 Au moment de la génération de la solution, les valeurs de propriété du récepteur de fonctionnalité dans la fonctionnalité et ses projets fusionnent pour définir les attributs ReceiverAssembly et ReceiverClass de l'élément de fonctionnalité dans le manifeste de fonctionnalité du fichier de solution SharePoint \(.wsp\).  Par conséquent, si les valeurs de propriété Assembly et Class Name d'un élément de projet et une fonctionnalité sont spécifiées, les valeurs de propriété de fonctionnalité et celles de l'élément de projet doivent correspondre.  Si ces valeurs ne correspondent pas, vous recevez une erreur de validation.  Si vous souhaitez qu'un élément de projet référence un assembly de récepteur de fonctionnalité autre que celui utilisé par sa fonctionnalité, déplacez\-le vers une autre fonctionnalité.  
  
 Si vous référencez un assembly de récepteur de fonctionnalité qui n'est pas déjà sur le serveur, vous devez également inclure le fichier d'assembly dans le package, car [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ne l'y ajoute pas.  Lorsque vous déployez la fonctionnalité, le fichier d'assembly est copié dans le [!INCLUDE[TLA#tla_gac](../sharepoint/includes/tlasharptla-gac-md.md)] du système ou le dossier Bin dans le répertoire physique SharePoint.  Pour plus d'informations, consultez [Comment : ajouter et supprimer des assemblys supplémentaires](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Pour plus d'informations sur les récepteurs des\= composant, consultez [Récepteur d'événements de fonctions](http://go.microsoft.com/fwlink/?LinkID=169574) et [Evénements de composant](http://go.microsoft.com/fwlink/?LinkID=169575)  
  
## Références de sortie de projet  
 La propriété Project Output References spécifie une dépendance, telle qu'un assembly, que votre élément de projet doit exécuter.  Par exemple, supposez que votre solution contient un projet BDC et un projet de classe.  Si le projet BDC a une dépendance sur l'assembly que le projet de classe génère, vous pouvez référencer l'assembly dans la propriété Project Output References du projet BDC.  Lorsque le projet BDC est empaqueté, l'assembly dépendant est inclus dans le package.  
  
 Les références de sortie de projet sont habituellement des assemblys, mais dans certains cas \(projets Silverlight\), il peut s'agir d'autres types de fichier.  
  
 Pour plus d'informations, consultez [Comment : ajouter une référence de sortie de projet](../sharepoint/how-to-add-a-project-output-reference.md).  
  
## Entrées de contrôle sécurisé  
 SharePoint fournit un mécanisme de sécurité, appelé entrées de contrôle sécurisé, pour limiter l'accès à certains contrôles par des utilisateurs non fiables.  Par conception, SharePoint permet aux utilisateurs non fiables de télécharger et de créer des pages ASPX sur le serveur SharePoint.  Pour empêcher ces utilisateurs d'ajouter du code unsafe aux pages ASPX, SharePoint limite leur accès aux *contrôles sécurisés*.  Les contrôles sécurisés sont des composants WebPart et des contrôles ASPX désignés comme sécurisés qui peuvent être utilisés par tout utilisateur sur votre site.  Pour plus d'informations, consultez [Étape 4 : Ajoutez le composant WebPart à la liste des contrôles sécurisée](http://go.microsoft.com/fwlink/?LinkID=171014).  
  
 Chaque élément de projet SharePoint dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] a une propriété nommée **Entrées de contrôle sécurisées** qui a deux sous\-propriétés booléennes : **Sécurisé** et **Protégé contre les scripts**.  La propriété sécurisée spécifie si des utilisateurs non approuvés peuvent accéder au contrôle.  La propriété Protégé contre les scripts spécifie si les utilisateurs non fiables peuvent afficher et modifier les propriétés d'un contrôle.  
  
 Les entrées de contrôle sécurisé sont référencées sur la base des assemblys.  Vous ajoutez des entrées de contrôle sécurisé à l'assembly d'un projet en les entrant dans la propriété **Entrées de contrôle sécurisé** de l'élément de projet.  Toutefois, vous pouvez également ajouter des entrées de contrôle sécurisé à l'assembly d'un projet via l'onglet **Avancé** du **Concepteur de packages** lorsque vous ajoutez un assembly supplémentaire au package.  Pour plus d'informations, consultez [Comment : marquer des contrôles comme étant des contrôles sécurisés](../sharepoint/how-to-mark-controls-as-safe-controls.md) ou [Enregistrement d'une assembly du composant WebPart en tant que contrôle sécurisé](http://go.microsoft.com/fwlink/?LinkID=171013).  
  
### Entrées XML pour les contrôles sécurisés  
 Lorsque vous ajoutez une entrée de contrôle sécurisé à un élément de projet ou à l'assembly du projet, une référence est écrite dans le manifeste du package au format suivant :  
  
```  
<Assemblies>  
    <Assembly Location="<assembly name>.dll"     
      DeploymentTarget="<'GlobalAssemblyCache' or 'WebApplication'">>  
        <SafeControls>  
            <SafeControl Assembly="<assembly name>.dll" Namespace=  
              "<SharePoint project name>" Safe="<true/false>"     
                TypeName="<control name>"   
                SafeAgainstScript="<true/false>" />  
        </SafeControls>  
    </Assembly>  
</Assemblies>  
```  
  
## Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Utilisation de modules pour inclure des fichiers dans la solution](../sharepoint/using-modules-to-include-files-in-the-solution.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)  
  
  