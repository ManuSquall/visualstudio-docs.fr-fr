---
title: "Conception des sous-types de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sous-types de projets, création"
ms.assetid: 405488bb-1362-40ed-b0f1-04a57fc98c56
caps.latest.revision: 32
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 32
---
# Conception des sous-types de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sous\-types de projet permettent de VSPackages étendre des projets avec Microsoft Build Engine \(MSBuild\).  L'utilisation du regroupement vous permet de réutiliser la partie du principal système de projet managé implémenté dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à personnaliser toujours le comportement pour un scénario particulier.  
  
 Les rubriques suivantes traitent la conception et implémentation de base de sous\-types de projet :  
  
-   création de sous\-type de projet.  
  
-   regroupement multiniveau.  
  
-   interfaces de prise en charge.  
  
## création de sous\-type de projet  
 L'initialisation d'un sous\-type de projet est accomplie en regroupant <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> et les principaux objets d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .  ce regroupement permet à un sous\-type de projet pour substituer ou améliorer la plupart des fonctions du projet de base.  Sous\-types de projet obtiennent la première possibilité de gérer des propriétés à l'aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, les commandes utilisant <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>, et la gestion d'élément de projet à l'aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>.  Sous\-types de projet peuvent également étendre :  
  
-   objets de configuration de projet.  
  
-   objets selon la configuration.  
  
-   Configuration\-indépendant parcourir des objets.  
  
-   objets Automation de projet.  
  
-   Collections de propriété automation de projet.  
  
 Pour plus d'informations sur l'extensibilité par des sous\-types de projet, consultez [Propriétés et méthodes étendus par les sous\-types de projets](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md).  
  
##### fichiers de stratégie  
 L'environnement de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fournit un exemple d'étendre le système de projet de base avec un sous\-type de projet dans son implémentation de fichiers de stratégie.  Un fichier de stratégie permet de personnaliser l'environnement de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]en gérant les fonctionnalités qui incluent la boîte de dialogue de l'explorateur de solutions, d' **Ajouter un projet** , la boîte de dialogue d' **Ajouter un nouvel élément** et la boîte de dialogue de **Propriétés** .  Sous\-type de stratégie substitue et améliore les fonctionnalités via <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>, `IOleCommandTarget` et des implémentations d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> .  
  
##### mécanisme de regroupement  
 Le mécanisme de regroupement de sous\-type du projet de l'environnement prend en charge plusieurs niveaux de regroupement, autorisant ainsi un sous\-type avancé à implémenter par plus d'assaisonnement un projet assaisonné.  En outre, les objets de prise en charge d'un sous\-type de projet, tels qu' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>, sont conçus pour autoriser plusieurs niveaux d'une couche.  Conformément à les contraintes les règles COM et COM de regroupement, des sous\-types de projet et les projets de base doivent être programmées de manière coopérative pour activer le sous\-type interne ou le projet de base de participer correctement à déléguer des appels de méthode et de la gestion des numéros de référence.  Autrement dit, le projet doit être regroupé environ doit être programmé pour prendre en charge le regroupement.  
  
 l'illustration suivante montre une représentation schématique d'un regroupement multiniveau de sous\-type de projet.  
  
 ![Graphique projectflavor à plusieurs niveaux Visual Studio](~/docs/extensibility/internals/media/vs_multilevelprojectflavor.gif "VS\_MultilevelProjectFlavor")  
sous\-type à plusieurs niveaux de projet  
  
 Un regroupement multiniveau de sous\-type de projet se compose de trois couches, un projet de base, qui est regroupé par un sous\-type de projet, effectue alors de synthèse par un sous\-type avancée de projet.  L'illustration se concentre sur certaines interfaces de prise en charge qui sont fournies en tant que partie de l'architecture de sous\-type de projet de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
##### mécanismes de déploiement  
 Parmi plusieurs fonctionnalités de base du système de projet améliorées par un sous\-type de projet sont des mécanismes de déploiement.  Un sous\-type de projet influence des mécanismes de déploiement en implémentant les interfaces de configuration \(telles qu' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg>\) qui sont récupérées en appelant QueryInterface sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider>.  Dans un scénario où le sous\-type de projet et sous\-type avancée de projet ajoutent des implémentations de configuration, le projet de base appelle `QueryInterface` sur `IUnknown`avancée de sous\-type de projet.  Si le sous\-type interne de projet contient l'implémentation de configuration laquelle le projet de base demande, le sous\-type avancée de projet délègue à l'implémentation fournie par le sous\-type interne de projet.  Comme un mécanisme pour rendre persistant l'état d'un niveau d'agrégation à une autre, tous les niveaux des sous\-types de projet implémentent <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> pour rendre persistantes les données XML connexes par génération dans les fichiers projet.  Pour plus d'informations, consultez [Données persistantes dans le fichier projet MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  <xref:EnvDTE80.IInternalExtenderProvider> est implémenté en tant que mécanisme pour récupérer des extendeurs automation des sous\-types de projet.  
  
 l'illustration suivante se concentre sur l'implémentation d'extendeur d'automation, la configuration de projet parcourent l'objet en particulier, utilisé par des sous\-types de projet pour étendre le système de projet de base.  
  
 ![Graphique d'extendeur automatique de la version d'un projet VS](~/docs/extensibility/internals/media/vs_projectflavorautoextender.gif "VS\_ProjectFlavorAutoExtender")  
extendeur Automation de sous\-type de projet.  
  
 Sous\-types de projet peuvent davantage étendre le système de projet de base en étendant le modèle objet Automation.  Celles\-ci sont définies comme une partie de l'objet Automation DTE et sont utilisées pour étendre l'objet Project, l'objet d' `ProjectItem` et l'objet d' `Configuration` .  Pour plus d'informations, consultez [Extension du modèle d'objet du projet de Base](../../extensibility/internals/extending-the-object-model-of-the-base-project.md).  
  
## regroupement multiniveau  
 Une implémentation de sous\-type de projet qui encapsule un sous\-type plus simple de projet doit être programmées de manière coopérative pour permettre au sous\-type interne de projet pour fonctionner correctement.  Une liste de responsabilités de programmation inclut :  
  
-   L'implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> de sous\-type de projet qui encapsule le sous\-type interne doit déléguer à <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> l'implémentation du sous\-type interne de projet pour <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> et des méthodes d' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> .  
  
-   L'implémentation d' <xref:EnvDTE80.IInternalExtenderProvider> de sous\-type de projet de wrapper doit la déléguer à celui de son sous\-type interne de projet.  En particulier, l'implémentation des besoins d' <xref:EnvDTE80.IInternalExtenderProvider.GetExtenderNames%2A> d'obtenir la chaîne des noms de sous\-type interne de projet puis de la concaténation des chaînes qu'il souhaite ajouter comme extendeurs.  
  
-   L'implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfgProvider> d'un sous\-type de projet de wrapper doit instancier l'objet d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg> de son sous\-type interne de projet et le gérer en tant que délégué privé, étant donné que seul l'objet de base de la configuration de projet du projet sait directement que l'objet de configuration de sous\-type de projet de wrapper existe.  Sous\-type externe de projet peut initialement choisir des interfaces de configuration qu'il souhaite gérer directement, puis délègue le reste de l'implémentation interne du sous\-type de projet d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg.get_CfgType%2A>.  
  
## interfaces de prise en charge  
 Le projet de base délègue les appels aux interfaces de prise en charge ajoutées par un sous\-type de projet, étendre les différents aspects de son implémentation.  Cela inclut étendre les objets de configuration de projet et d'objets individuels de l'Explorateur de propriétés.  Ces interfaces sont récupérées en appelant `QueryInterface` sur `punkOuter` \(un pointeur vers `IUnknown`\) de l'agrégation surface de sous\-type de projet.  
  
|Interface|sous\-type de projet|  
|---------------|--------------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFlavorCfg>|permet le sous\-type de projet à :<br /><br /> -   fournir une implémentation de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>.<br />-   Contrôlez le lancement du débogueur et permet au sous\-type de projet pour fournir sa propre implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>.<br />-   Désactivez l'évaluation d'une expression au moment de le design en gérant correctement le cas d' `DBGLAUNCH_DesignTimeExprEval` dans son implémentation d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.QueryDebugLaunch%2A>.|  
|<xref:EnvDTE80.IInternalExtenderProvider>|permet le sous\-type de projet à :<br /><br /> -   Étendez <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> de project pour ajouter ou supprimer les propriétés indépendantes de configuration du projet.<br />-   étendez l'objet Automation de projet \(<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>\) du projet.<br /><br /> Les valeurs de propriété ci\-dessus sont récupérées l'énumération d' <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> .|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject>|Permet le sous\-type de projet au mappage vers l'objet d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> donné la configuration de projet parcourent l'objet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBrowseObject>|Permet le sous\-type de projet au mappage vers <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> ou l'objet d' `VSITEMID` , selon la configuration de projet parcourent l'objet.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>|Permet au sous\-type de projet pour rendre des données structurées arbitraires XML dans le fichier projet \(.vbproj ou .csproj\).  Ces données n'est pas visible à MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>|permet le sous\-type de projet à :<br /><br /> -   Ajoutez les nouvelles propriétés MSBuild à rendre persistants.<br />-   Supprimez les propriétés inutiles MSBuild.<br />-   Requête d'une valeur actuelle d'une propriété MSBuild.<br />-   Modifiez la valeur actuelle d'une propriété MSBuild.|  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2>