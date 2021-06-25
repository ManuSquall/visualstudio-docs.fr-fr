---
title: Constantes IDE | Microsoft Docs
description: La classe VSConstants fournit des constantes spécifiques à l’environnement de développement intégré (IDE) qui ont été précédemment définies uniquement dans les fichiers d’en-tête.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 802de0fd29d909320040667f972de422595bdd4f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904966"
---
# <a name="ide-constants"></a>Constantes IDE

La <xref:Microsoft.VisualStudio.VSConstants> classe fournit des constantes qui sont spécifiques à l’environnement de développement intégré (IDE) et qui ont été précédemment définies uniquement dans les fichiers d’en-tête.

## <a name="logical-and-physical-views"></a>Vues logiques et physiques

|Valeur|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`les gestionnaires doivent passer cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour accéder à la boîte de dialogue **Ouvrir avec** , dans ce cas sur les affichages de code possibles.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>les `cmdidOpenWith` gestionnaires passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir la boîte de dialogue **Ouvrir avec** , dans ce cas rempli avec les <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> vues de débogage possibles qui mappent à la même vue que <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`les gestionnaires passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir la boîte de dialogue **Ouvrir avec** , dans ce cas pour afficher les vues du concepteur de **formulaires** .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>les `cmdidOpenWith` gestionnaires passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir la boîte de dialogue **Ouvrir avec** , dans ce cas la vue par défaut/principale de la fabrique d’éditeur.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`les gestionnaires passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode pour obtenir la boîte de dialogue **Ouvrir avec** , dans ce cas pour une vue document ou éditeur de texte de données.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>les `cmdidOpenWith` gestionnaires passent cette valeur à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> méthode qui invite l’utilisateur à choisir la vue définie par l’utilisateur à utiliser.|

## <a name="editor-factory-flags"></a>Indicateurs de fabrique d’éditeur

|Valeur|Description|
|-----------|-----------------|
|[CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Un indicateur obsolète combiné au niveau du bit comme premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> méthode.|
|[CEF. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Combinaison au niveau du bit en tant que premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> méthode, qui indique que la fabrique d’éditeur doit effectuer les corrections nécessaires.|
|[CEF. OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Combinaison au niveau du bit en tant que premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> méthode, cet indicateur s’exclut mutuellement de [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF. Sans assistance](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Combinaison au niveau du bit en tant que premier paramètre de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> méthode, ce qui indique que la fabrique d’éditeur doit créer l’éditeur sans afficher d’interface utilisateur.|

## <a name="visual-studio-errors"></a>Erreurs Visual Studio

|Valeur|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Constante retournée par les interfaces au comportement asynchrone quand l’objet en question est déjà occupé|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|HRESULT d’erreur qui est spécifique à Visual Studio pour « données de document incompatibles ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique « package non chargé ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|HRESULT d’erreur qui est spécifique à Visual Studio et qui indique que le « projet existe déjà ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|HRESULT d’erreur qui est spécifique à Visual Studio et qui indique « échec de la configuration du projet ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|HRESULT d’erreur qui est spécifique à Visual Studio et qui indique « projet non chargé ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique « solution déjà ouverte ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Une erreur HRESULT qui est spécifique à Visual Studio et qui indique « la solution n’est pas ouverte ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Retourné par les interfaces de build qui ont des paramètres pour la spécification d’un tableau à partir de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interface, mais l’implémentation peut appliquer la méthode uniquement à toutes les sorties.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|La <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> méthode retourne cette valeur si le document a un format qui ne peut pas être ouvert dans l’éditeur.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Valeur HRESULT qui indique que l’utilisateur a cliqué sur le bouton précédent dans un Assistant Visual Studio.|

## <a name="visual-studio-constants"></a>Constantes Visual Studio

|Valeur|Description|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|HRESULT d’erreur qui est spécifique à Visual Studio et qui indique « projet transféré ».|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Constante qui est spécifique à Visual Studio pour un « marqueur de boîte à outils ».|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Constante qui est spécifique à Visual Studio pour diffuser un message de notification via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode qui indique le début de la modalité.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Constante qui est spécifique à Visual Studio pour diffuser un message de notification via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode qui indique la fin de la modalité.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Constante qui est spécifique à Visual Studio pour diffuser un message de notification via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> méthode indiquant que les mesures de la barre de commandes ont changé.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Constante spécifique à Visual Studio qui indique qu’aucun cookie n’a été défini.|
|[VSITEMID. Pli](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identificateur d’élément Visual Studio qui représente l’absence d’un élément de projet. Cette valeur est utilisée lorsqu’il n’y a aucune sélection actuelle.|
|[VSITEMID. Causes](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identificateur d’élément Visual Studio qui représente la racine d’une hiérarchie de projet et qui est utilisé pour identifier l’intégralité de la hiérarchie, par opposition à un seul élément.|
|[VSITEMID. Sélection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identificateur d’élément Visual Studio qui représente le ou les éléments actuellement sélectionnés, qui peuvent inclure la racine de la hiérarchie.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Décrit le composant de l’IDE qui vient d’être sélectionné, dans un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> appel, par exemple.

|Constante|Valeur|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement. StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement. UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement. UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement. WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Constantes utilisées pour indiquer un nouvel état de sélection.

|Constante|Valeur|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Constantes de la boîte de dialogue Sélecteur de composants

|Constante|Valeur|
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
