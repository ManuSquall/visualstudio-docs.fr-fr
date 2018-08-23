---
title: Constantes de l’IDE | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
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
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4f2cf01bcc8b2854eb1e4c3c711af524a8480bdc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42635130"
---
# <a name="ide-constants"></a>Constantes de l’IDE

Le <xref:Microsoft.VisualStudio.VSConstants> classe fournit des constantes qui sont spécifiques à l’environnement de développement intégré (IDE) et qui ont été précédemment défini uniquement dans les fichiers d’en-tête.

## <a name="logical-and-physical-views"></a>Vues logiques et physiques

|Value|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires doivent passer cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir le **ouvrir avec** boîte de dialogue, dans ce cas sur les vues de code potentiels.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de cette valeur à passer le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir le **ouvrir avec** boîte de dialogue, dans ce cas rempli avec possible <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> débogage des vues qui correspondent au même affichage que <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de passer cette valeur pour le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir le **ouvrir avec** boîte de dialogue, dans ce cas **afficher le formulaire** vues du concepteur.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de passer cette valeur pour le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir le **ouvrir avec** boîte de dialogue, dans ce cas, l’affichage principal/par défaut de la fabrique d’éditeur.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de passer cette valeur pour le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir le **ouvrir avec** boîte de dialogue, dans ce cas pour un affichage d’éditeur de texte document ou de données.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestionnaires de cette valeur à passer le <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode qui invite l’utilisateur de choisir le mode défini par l’utilisateur à utiliser.|

## <a name="editor-factory-flags"></a>Indicateurs de fabrique d’éditeur

|Value|Description|
|-----------|-----------------|
|[CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Un indicateur obsolète a combiné or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> (méthode).|
|[CEF. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Combinés or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, méthode, cela indique la fabrique d’éditeur doit effectuer les corrections nécessaires.|
|[CEF. OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Combinés or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> , cet indicateur est mutuellement exclusive de [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF. En mode silencieux](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Combinés or comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> (méthode), cela indique la fabrique d’éditeur doit créer l’éditeur sans afficher d’interface utilisateur (IU).|

## <a name="visual-studio-errors"></a>Erreurs de Visual Studio

|Value|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Constante retournée par les interfaces à un comportement asynchrone lorsque l’objet en question dans déjà occupé|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Une erreur HRESULT est spécifique à Visual Studio pour « données de document incompatibles ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Une erreur HRESULT est spécifique à Visual Studio et qui indique « Package non chargé ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Une erreur HRESULT est spécifique à Visual Studio et qui indique que le « Projet existe déjà. »|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique « Échec de la configuration de projet. »|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Une erreur HRESULT est spécifique à Visual Studio et qui indique « Projet non chargé ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Une erreur HRESULT est spécifique à Visual Studio et qui indique « Solution déjà ouvert. »|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique « Solution pas ouvrir ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Retourné par les interfaces de génération qui ont des paramètres pour spécifier un tableau à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interface, mais l’implémentation peut s’appliquent uniquement la méthode à toutes les sorties.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Le <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> méthode renvoie cette valeur si le document a un format qui ne peut pas être ouvert dans l’éditeur.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Valeur HRESULT qui indique que l’utilisateur a activé le bouton précédent dans un Assistant de Visual Studio.|

## <a name="visual-studio-constants"></a>Constantes de Visual Studio

|Value|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Une erreur HRESULT est spécifique à Visual Studio et qui indique « Projet transféré ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Une constante qui est spécifique à Visual Studio pour un « marqueur de boîte à outils ».|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Une constante qui est spécifique à Visual Studio pour diffuser un message de notification via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode qui indique le début de la modalité.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Une constante qui est spécifique à Visual Studio pour diffuser un message de notification via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode qui indique la fin de la modalité.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Une constante qui est spécifique à Visual Studio pour diffuser un message de notification via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode indiquant que les métriques de barre de commande ont été modifiés.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Constante qui est spécifique à Visual Studio qui indique qu’aucun cookie n’a pas été défini.|
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Un identificateur d’élément Visual Studio qui représente l’absence d’un élément de projet. Cette valeur est utilisée lors de l’absence de sélection actuel.|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Un identificateur d’élément Visual Studio qui représente la racine d’une hiérarchie de projet et est utilisé pour identifier l’ensemble de la hiérarchie, par opposition à un seul élément.|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Un identificateur d’élément Visual Studio qui représente l’élément actuellement sélectionné ou les éléments, ce qui peuvent inclure la racine de la hiérarchie.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Décrit les composants de l’IDE a vient d’être sélectionné, dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> appeler, par exemple.

|Constante|Value|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0 x 2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0 x 4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0 x 3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0 x 0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0 x 5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0 x 1|

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

## <a name="component-selector-dialog-constants"></a>Constantes de boîte de dialogue de sélecteur de composant

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