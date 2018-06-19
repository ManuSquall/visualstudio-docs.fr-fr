---
title: Comportement de nouveau ou modifié avec les adaptateurs d’éditeur | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22028b1b2725f184c3d5748f2885a17d4bff0c60
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148660"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Comportement de nouveau ou modifié avec les adaptateurs d’éditeur
Si vous mettez à jour le code qui a été écrit par rapport aux versions antérieures de l’éditeur principal de Visual Studio et que vous prévoyez d’utiliser l’éditeur adaptateurs (ou des shims) au lieu d’utiliser la nouvelle API, vous devez connaître les différences suivantes dans le comportement de l’éditeur de cartes en ce qui concerne l’éditeur principal précédent.  
  
## <a name="features"></a>Fonctionnalités  
  
#### <a name="using-setsite"></a>À l’aide de la fonction SetSite()  
 Vous devez appeler <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> lorsque vous CoCreate mémoires tampons de texte, des affichages de texte et le code windows avant d’effectuer d’autres opérations sur les. Toutefois, cela n’est pas nécessaire si vous utilisez la <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> à les créer, étant donné que les méthodes de ce service Create() eux-mêmes appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hébergement IVsCodeWindow et IVsTextView dans votre propre contenu.  
 Vous pouvez héberger les deux <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dans votre propre contenu en utilisant le mode de Win32 ou WPF. Toutefois, gardez à l’esprit qu’il existe des différences dans les deux modes.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>À l’aide de versions de Win32 et WPF de IVsCodeWindow  
 La fenêtre de l’éditeur de code est dérivée de <xref:Microsoft.VisualStudio.Shell.WindowPane>, qui implémente l’ancienne Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> de l’interface, ainsi que la nouvelle WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interface. Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> pour créer un environnement d’hébergement basés sur HWND, méthode ou la <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> méthode pour créer un environnement d’hébergement WPF. L’éditeur sous-jacente utilise toujours WPF, mais vous pouvez créer le type de volet de fenêtre adapté à vos exigences d’hébergement, si vous incorporez directement dans votre propre contenu de ce volet de fenêtre.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>À l’aide des versions de IVsTextView Win32 et WPF  
 Vous pouvez définir un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> au mode de Win32 ou WPF.  
  
 Lorsqu’une fabrique d’éditeur crée une vue de texte, par défaut, il est hébergé à l’intérieur d’un HWND, et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> retourne un HWND. Vous ne devez pas utiliser ce mode pour incorporer l’éditeur à l’intérieur d’un contrôle WPF.  
  
 Pour définir une vue de texte en mode de WPF, vous devez appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> et transmettez <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> comme indicateurs d’un de l’initialisation de le `InitView` paramètre. Vous pouvez obtenir le <xref:System.Windows.FrameworkElement> en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Mode WPF est différent du mode Win32 de deux manières. Tout d’abord, l’affichage de texte peut être hébergé dans un contexte WPF. Vous pouvez accéder au volet WPF en effectuant un cast du <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> à <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> et en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Ensuite, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> toujours retourne un HWND, mais que ce HWND peut être utilisé uniquement pour vérifier sa position et de définir le focus sur celui-ci. Vous ne devez pas utiliser ce HWND pour répondre à un message WM_PAINT, car elle n’affecte pas la façon dont l’éditeur peint la fenêtre. Ce HWND est présent uniquement pour faciliter la transition vers le nouveau code de l’éditeur au moyen de cartes. Il est fortement recommandé que vous ne devez pas utiliser `VIF_NO_HWND_SUPPORT` si votre composant requiert un HWND fonctionnent, en raison des limitations dans le HWND retourné à partir de `GetWindowHandle` alors que dans ce mode.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Passage de tableaux en tant que paramètres dans le code natif  
 Il existe de nombreuses méthodes dans l’API de l’éditeur hérité qui ont des paramètres qui incluent un tableau et son nombre. Les exemples sont :  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Si vous appelez ces méthodes en code natif, vous devez passer un seul élément à la fois. Si vous passez plusieurs éléments, l’appel rejeté en raison de problèmes avec l’implémentation d’interopérabilité principale.  
  
 Le problème est plus complexe avec des méthodes telles que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Chaque fois que cette méthode est appelée, elle efface la liste précédente des types de marqueur ignorés, donc il n’est pas possible de simplement appeler cette méthode trois fois avec trois types de marqueur différent. La seule solution est d’appeler cette méthode uniquement dans le code managé.  
  
#### <a name="threading"></a>Thread  
 Vous devez toujours appeler l’adaptateur de la mémoire tampon à partir du thread d’interface utilisateur. La carte de la mémoire tampon est un objet géré, ce qui signifie que contourne appel dans celui-ci à partir de code managé marshaling COM et votre appel n’est pas automatiquement marshalée pour le thread d’interface utilisateur.  Si vous appelez l’adaptateur de la mémoire tampon à partir d’un thread d’arrière-plan, vous devez utiliser <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ou une méthode similaire.  
  
#### <a name="lockbuffer-methods"></a>Méthodes LockBuffer  
 Toutes les méthodes LockBuffer() sont déconseillés. Les exemples sont :  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Valider des événements  
 Valider les événements ne sont pas pris en charge. Appel d’une méthode qui indique qu’il contient pour ces événements provoque la méthode retourner un code d’échec.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 Le <xref:EnvDTE.TextEditorEvents> ne déclenchent pas Commit(). Au lieu de cela, ils sont déclenchés lors de chaque modification de texte.  
  
#### <a name="text-markers"></a>Marqueurs de texte  
 Vous devez appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> objets lorsque vous les supprimez. Dans les versions précédentes, vous deviez uniquement les indicateurs de version.  
  
#### <a name="line-numbers"></a>Numéros de ligne  
 Pour une variété de méthodes sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>pas numéros de ligne que le facteur de mise en relief et de retour, comme dans Visual Studio 2008, les numéros de ligne correspondent aux numéros de ligne de mémoire tampon sous-jacente.  
  
 Les méthodes affectées sont les suivantes (la liste n’est pas exhaustive) :  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>mode Plan  
 Les clients de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> s’affiche uniquement les régions en mode plan qui ont été ajoutées à l’aide de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>ou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Ils ne verront pas régions ad hoc, car ils ne sont pas ajoutés par les cartes de l’éditeur. De même, ces clients ne verront pas ajoutées par les langages (y compris les langages c# et C++) qui utilisent le nouveau code de l’éditeur, plutôt que les adaptateurs de l’éditeur de régions en mode plan.  
  
#### <a name="line-heights"></a>Hauteur des lignes  
 Dans le nouvel éditeur de lignes de texte peuvent avoir des hauteurs différentes, selon la taille de police et les transformations de ligne possibles qui peut se déplacer à la ligne par rapport à d’autres lignes. La hauteur de ligne retournée par les méthodes telles que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> correspond à la hauteur d’une ligne avec aucune ligne les transformations appliquées à l’aide de la taille de police par défaut. Cette hauteur peut ou peut ne pas refléter la hauteur réelle d’une ligne dans la vue.  
  
#### <a name="eventing-and-undo"></a>Gestion des événements et l’annulation  
 Dans l’éditeur de nouveau, la vue se poursuit effectuer des opérations telles que le rendu et le déclenchement d’événements en permanence, même si un cluster d’annulation est ouvert. Ce comportement est différent de celui de vues hérités, ce qui n’a pas effectué ces opérations jusqu'à ce qu’après la fermeture du cluster d’annulation.  
  
#### <a name="intellisense"></a>IntelliSense  
  
-   Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> méthode échouera si vous passez dans une classe qui n’implémente pas <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> ou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Personnalisé Win32 owner-drawn les fenêtres contextuelles ne sont plus prises en charge.  
  
#### <a name="smarttags"></a>Balises actives  
 Il n’existe aucune prise en charge de l’adaptateur pour les balises actives, créée avec <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> interfaces.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> n’est pas implémentée.  
  
## <a name="unimplemented-methods"></a>Méthodes non implémentées  
 Certaines méthodes n’ont pas été implémentées dans la carte de mémoire tampon de texte, adaptateur de vue de texte, adaptateur de couche de texte.  
  
|Interface|Non implémenté|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` n’est pas implémentée.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> est implémenté dans les cartes, mais elle est ignorée par l’interface utilisateur en mode plan.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> est implémenté dans les cartes, mais elle est ignorée par l’interface utilisateur en mode plan.|