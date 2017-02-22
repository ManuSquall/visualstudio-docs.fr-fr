---
title: "Constantes de l&#39;IDE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE, erreurs"
  - "Affichages logiques"
  - "erreurs (Visual Studio), IDE"
  - "Constantes de contexte de l'interface utilisateur"
  - "constantes, l'IDE de Visual Studio"
  - "IDE, constantes"
  - "vues physiques"
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Constantes de l&#39;IDE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La <xref:Microsoft.VisualStudio.VSConstants> classe fournit des constantes qui sont spécifiques à l'environnement de développement intégré \(IDE\) et qui ont été précédemment définies uniquement dans les fichiers d'en\-tête.  
  
## Affichages logique et physique  
  
|Valeur|Description|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires doivent passer cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode permettant d'obtenir le **Ouvrir avec** boîte de dialogue, dans ce cas sur les vues de Code possible.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode permettant d'obtenir le **Ouvrir avec** boîte de dialogue, dans ce cas rempli avec possible <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging> débogage vues qui correspondent à la même vue en tant que <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Designer>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode permettant d'obtenir le **Ouvrir avec** boîte de dialogue, dans ce cas **Afficher le formulaire** vues du concepteur.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Primary>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode permettant d'obtenir le **Ouvrir avec** boîte de dialogue, dans ce cas, la vue par défaut\/principal de la fabrique d'éditeur.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_TextView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode permettant d'obtenir le **Ouvrir avec** la boîte de dialogue pour une vue de l'éditeur de texte document ou données.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_UserChooseView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode qui demande à l'utilisateur de choisir le mode défini par l'utilisateur à utiliser.|  
  
## Indicateurs de fabrique d'éditeur  
  
|Valeur|Description|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>|Un indicateur obsolète combinées or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> méthode.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENASNEW>|Combinés or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, méthode, cela indique la fabrique d'éditeur doit effectuer les corrections nécessaires.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENFILE>|Combinés or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> \(méthode\), cet indicateur est mutuellement mutuellement <xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_SILENT>|Combinés or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> \(méthode\), cela indique la fabrique d'éditeur doit créer l'éditeur sans afficher d'interface utilisateur \(IU\).|  
  
## Erreurs de Visual Studio  
  
|Valeur|Description|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Une constante retournée par les interfaces au comportement asynchrone lorsque l'objet en question dans déjà occupé|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Une erreur HRESULT spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour « données de document Incompatible ».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Une erreur HRESULT spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Package » n'a ne pas chargé.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Une erreur HRESULT spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique que le « Projet existe déjà. »|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Une erreur HRESULT spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Échec de la configuration du projet. »|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Une erreur HRESULT spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Projet n'a ne pas chargé ».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Une erreur HRESULT spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Solution déjà ouverte. »|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Une erreur HRESULT spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Solution n'est pas ouverte. »|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Retourné par les interfaces de build qui ont des paramètres pour la spécification d'un tableau à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interface, mais l'implémentation peut s'appliquent uniquement la méthode à toutes les sorties.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Le <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> méthode renvoie cette valeur si le document a un format qui ne peut pas être ouvert dans l'éditeur.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Une valeur HRESULT qui indique que l'utilisateur cliquait sur le bouton précédent dans un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Assistant.|  
  
## Constantes de Visual Studio  
  
|Valeur|Description|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Une erreur HRESULT spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Projet transféré ».|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Constante qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour un « marqueur de boîte à outils ».|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Constante qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour la diffusion d'un message de notification via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode qui indique le début d'une modalité.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Constante qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour la diffusion d'un message de notification via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode qui indique la fin d'une modalité.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Constante qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour la diffusion d'un message de notification via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode indiquant que les mesures de barre de commande ont été modifiés.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Constante qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui indique qu'un cookie n'a pas été défini.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>|Un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificateur d'élément qui représente l'absence d'un élément de projet. Cette valeur est utilisée lorsqu'il n'y a aucun sélection.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>|Un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificateur d'élément qui représente la racine de la hiérarchie d'un projet et est utilisé pour identifier l'ensemble de la hiérarchie, par opposition à un seul élément.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>|Un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificateur d'élément qui représente l'élément actuellement sélectionné ou les éléments, ce qui peuvent inclure à la racine de la hiérarchie.|  
  
## IVsSelectionEvents  
 Décrit les composants de l'IDE a simplement été sélectionné, dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> appeler, par exemple.  
  
|Constante|Valeur|  
|---------------|------------|  
|<xref:Microsoft.VisualStudio.VSConstants.DocumentFrame>|0 x 2|  
|<xref:Microsoft.VisualStudio.VSConstants.PropertyBrowserSID>|0 x 4|  
|<xref:Microsoft.VisualStudio.VSConstants.StartupProject>|0 x 3|  
|<xref:Microsoft.VisualStudio.VSConstants.UndoManager>|0 x 0|  
|<xref:Microsoft.VisualStudio.VSConstants.UserContext>|0 x 5|  
|<xref:Microsoft.VisualStudio.VSConstants.WindowFrame>|0 x 1|  
  
## VSSELELEMID  
 Constantes utilisées pour indiquer un nouvel état de sélection.  
  
|Constante|Valeur|  
|---------------|------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|  
  
## Constantes de boîte de dialogue Sélecteur de composants  
  
|Constante|Valeur|  
|---------------|------------|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM\_USER \+ 1280|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM\_USER \+ 1281|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM\_USER \+ 1290|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM\_USER \+ 1287|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM\_USER \+ 1285|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM\_USER \+ 1288|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM\_USER \+ 1286|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM\_USER \+ 1289|  
  
## Voir aussi  
 [Commandes définies par l'IDE pour l'extension des systèmes de projet](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)