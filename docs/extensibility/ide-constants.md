---
title: IDE Constants - France Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2eddac1cc7d7e616deb197752adf41a4d68d15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710500"
---
# <a name="ide-constants"></a>Constantes IDE

La <xref:Microsoft.VisualStudio.VSConstants> classe fournit des constantes spécifiques à l’environnement de développement intégré (IDE) et qui n’étaient auparavant définies que dans les fichiers d’en-tête.

## <a name="logical-and-physical-views"></a>Points de vue logiques et physiques

|Valeur|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` les gestionnaires doivent transmettre cette <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> valeur à la méthode pour obtenir la boîte de dialogue **Open With,** dans ce cas sur les vues de code possibles.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` les gestionnaires passent cette <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> valeur à la méthode pour obtenir la boîte de <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> dialogue **Open With,** dans ce cas peuplé de vues de débogage possibles qui cartographient à la même vue que <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` les gestionnaires passent cette <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> valeur à la méthode pour obtenir la boîte de dialogue **Open With,** dans ce cas, pour afficher les vues de concepteur **de forme.**|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` les gestionnaires passent cette <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> valeur à la méthode pour obtenir la boîte de dialogue **Open With,** dans ce cas, la vue par défaut / primaire de l’usine d’éditeur.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` les gestionnaires transmettent cette <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> valeur à la méthode pour obtenir la boîte de dialogue **Open With,** dans ce pour un document ou une vue d’éditeur de texte de données.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` les gestionnaires transmettent cette <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> valeur à la méthode qui incite l’utilisateur à choisir la vue définie par l’utilisateur à utiliser.|

## <a name="editor-factory-flags"></a>Indicateurs de l’usine de rédacteur en chef

|Valeur|Description|
|-----------|-----------------|
|[Cef. CloneFile CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Un drapeau obsolète combiné bitwise comme <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> le premier paramètre de la méthode.|
|[Cef. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Combiné bitwise comme le <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>premier paramètre de la méthode , cela indique l’usine d’éditeur devrait effectuer les correctifs nécessaires.|
|[Cef. OpenFile (OpenFile)](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Combiné bitwise comme premier <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> paramètre de la méthode, ce drapeau est mutuellement exclusif de [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[Cef. Silencieux](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Combiné bitwise comme le <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> premier paramètre de la méthode, cela indique que l’usine d’éditeur devrait créer l’éditeur sans afficher une interface utilisateur (interface utilisateur).|

## <a name="visual-studio-errors"></a>Erreurs de studio visuel

|Valeur|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Une constante retournée par les interfaces à un comportement asynchrone lorsque l’objet en question dans déjà occupé|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Une erreur HRESULT qui est spécifique à Visual Studio pour "Données de documents incompatibles".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique "Package pas chargé."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique que le "Projet existe déjà."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique "la configuration du projet a échoué."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique "Projet non chargé."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique "Solution déjà ouverte."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique "Solution pas ouverte."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Retourné par des interfaces de construction qui ont <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> des paramètres pour spécifier un tableau de l’interface, mais la mise en œuvre ne peut appliquer la méthode à toutes les sorties.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|La <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> méthode renvoie cette valeur si le document a un format qui ne peut pas être ouvert dans l’éditeur.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Une valeur HRESULT qui indique que l’utilisateur a appuyé sur le bouton arrière d’un assistant Visual Studio.|

## <a name="visual-studio-constants"></a>Constants Visual Studio

|Valeur|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique "Projet transmis."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Une constante spécifique à Visual Studio pour un " marqueur Toolbox ".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Une constante spécifique à Visual Studio pour la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> diffusion d’un message de notification via la méthode qui indique le début de la modalité.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Une constante spécifique à Visual Studio pour la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> diffusion d’un message de notification via la méthode qui indique la fin de la modalité.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Une constante spécifique à Visual Studio pour la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> diffusion d’un message de notification via la méthode indiquant que les mesures de la barre de commande ont changé.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Une constante spécifique à Visual Studio qui indique qu’un cookie n’a pas été défini.|
|[C’EST VSITEMID. Nil Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Un identifiant d’élément Visual Studio qui représente l’absence d’un élément de projet. Cette valeur est utilisée lorsqu’il n’y a pas de sélection actuelle.|
|[C’EST VSITEMID. Racine](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Un identifiant d’élément Visual Studio qui représente la racine d’une hiérarchie de projet et est utilisé pour identifier l’ensemble de la hiérarchie, par opposition à un seul élément.|
|[C’EST VSITEMID. Sélection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Un identifiant d’élément Visual Studio qui représente l’élément ou les éléments actuellement sélectionnés, qui peut inclure la racine de la hiérarchie.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Décrit quelle composante de l’IDE vient <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> d’être sélectionnée, par exemple lors d’un appel.

|Constant|Valeur|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SélectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Constantes utilisées pour indiquer un nouvel état de sélection.

|Constant|Valeur|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Constantes de dialogue de sélecteur de composants

|Constant|Valeur|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER 1280 euros|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER 1281 euros|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER 1290 euros|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER 1287 euros|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER 1285 euros|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER 1288 euros|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER 1286 euros|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER 1289 euros|

## <a name="see-also"></a>Voir aussi

- [Commandes définies par l’IDE pour l’extension des systèmes de projet](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
