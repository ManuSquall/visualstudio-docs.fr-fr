---
title: Les constantes IDE | Documents Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: ''
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0184cd4654f07b407a12ca12f0ff9da39c9ec890
ms.sourcegitcommit: 768118d470da9c7164d2f23ca918dfe26a4be72f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="ide-constants"></a>Constantes de l’IDE

La <xref:Microsoft.VisualStudio.VSConstants> classe fournit des constantes qui sont spécifiques à l’environnement de développement intégré (IDE) et qui ont été précédemment défini uniquement dans les fichiers d’en-tête.

## <a name="logical-and-physical-views"></a>Affichages logique et physique

|Value|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires doivent passer cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir le **ouvrir avec** boîte de dialogue, dans ce cas sur les vues de Code possibles.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir le **ouvrir avec** boîte de dialogue, dans ce cas rempli avec possible <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> débogage des vues qui correspondent à la même vue comme <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir le **ouvrir avec** boîte de dialogue, dans ce cas à **afficher le formulaire** vues du concepteur.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir le **ouvrir avec** boîte de dialogue, dans ce cas, la vue par défaut/primaire de la fabrique d’éditeur.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir le **ouvrir avec** la boîte de dialogue pour une vue de l’éditeur de texte document ou de données.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode qui invite l’utilisateur de choisir le mode défini par l’utilisateur à utiliser.|

## <a name="editor-factory-flags"></a>Indicateurs de fabrique d’éditeur

|Value|Description|
|-----------|-----------------|
|[CEF.CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Un indicateur obsolète combinées or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> (méthode).|
|[CEF.OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Combinées or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, méthode, cela indique la fabrique d’éditeur doit effectuer les corrections nécessaires.|
|[CEF.OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Combinées or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> , cet indicateur est mutuellement exclusive de [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF.Silent](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Combinées or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> (méthode), cela indique la fabrique d’éditeur doit créer l’éditeur sans afficher d’interface utilisateur (IU).|

## <a name="visual-studio-errors"></a>Erreurs de Visual Studio

|Value|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Une constante retournée par les interfaces au comportement asynchrone lorsque l’objet en question dans déjà occupé|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Une erreur HRESULT qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour « données de document Incompatible ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Une erreur HRESULT qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Le Package n’a ne pas chargé ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Une erreur HRESULT qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique que le « Projet existe déjà. »|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Une erreur HRESULT qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Échec de la configuration du projet. »|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Une erreur HRESULT qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Projet n’a ne pas chargé. »|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Une erreur HRESULT qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Solution déjà ouverte. »|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Une erreur HRESULT qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Solution n’est pas ouverte. »|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Retourné par les interfaces de build qui ont des paramètres pour la spécification d’un tableau à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interface, mais l’implémentation peut s’appliquent uniquement la méthode à toutes les sorties.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Le <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> méthode renvoie cette valeur si le document a un format qui ne peut pas être ouvert dans l’éditeur.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Une valeur HRESULT qui indique que l’utilisateur clique sur le bouton précédent dans un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Assistant.|

## <a name="visual-studio-constants"></a>Constantes de Visual Studio

|Value|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Une erreur HRESULT qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et qui indique « Projet transféré ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Constante qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour un « marqueur de boîte à outils ».|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Constante qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour la diffusion d’un message de notification via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode qui indique le début d’une modalité.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Constante qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour la diffusion d’un message de notification via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode indiquant la fin de modalité.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Constante qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pour la diffusion d’un message de notification via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode indiquant que les mesures de barre de commandes ont été modifiés.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Constante qui est spécifique à [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qui indique qu’un cookie n’a pas été défini.|
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificateur d’élément qui représente l’absence d’un élément de projet. Cette valeur est utilisée lorsqu’il n’existe pas de sélection.|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificateur d’élément qui représente la racine d’une hiérarchie de projet et est utilisé pour identifier l’ensemble de la hiérarchie, par opposition à un seul élément.|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificateur d’élément qui représente l’élément actuellement sélectionné ou les éléments, ce qui peuvent inclure à la racine de la hiérarchie.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Décrit le composant de l’IDE a simplement été sélectionné, dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> appeler, par exemple.

|Constante|Value|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Constantes utilisées pour indiquer un nouvel état de sélection.

|Constante|Value|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Constantes de boîte de dialogue de sélection de composant

|Constante|Value|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>Voir aussi

- [Commandes définies par l’IDE pour l’extension des systèmes de projet](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)