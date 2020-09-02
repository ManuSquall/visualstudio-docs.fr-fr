---
title: Comportement nouveau ou modifié avec les adaptateurs d’éditeur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc7ddaf7ec67a1e33248d5ce424868849200d3e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194178"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Comportement nouveau ou modifié avec les adaptateurs de l’éditeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous mettez à jour du code écrit sur des versions antérieures de l’éditeur de base de Visual Studio et que vous envisagez d’utiliser les adaptateurs d’éditeur (ou shims) au lieu d’utiliser la nouvelle API, vous devez connaître les différences suivantes dans le comportement des adaptateurs d’éditeur par rapport à l’éditeur principal précédent.  
  
## <a name="features"></a>Fonctionnalités  
  
#### <a name="using-setsite"></a>Utilisation de SetSite ()  
 Vous devez appeler <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> lorsque vous cocréez des mémoires tampons de texte, des vues de texte et des fenêtres de code avant d’effectuer d’autres opérations sur ceux-ci. Toutefois, cela n’est pas nécessaire si vous utilisez <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> pour les créer, car les méthodes Create () de ce service appellent elles-mêmes <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> .  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hébergement de IVsCodeWindow et IVsTextView dans votre propre contenu  
 Vous pouvez héberger <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dans votre propre contenu en utilisant le mode Win32 ou le mode WPF. Toutefois, vous devez garder à l’esprit qu’il existe des différences entre les deux modes.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Utilisation des versions Win32 et WPF de IVsCodeWindow  
 La fenêtre de code de l’éditeur est dérivée de <xref:Microsoft.VisualStudio.Shell.WindowPane> , qui implémente l’ancienne interface Win32, ainsi <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> que la nouvelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interface WPF. Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> méthode pour créer un environnement d’hébergement HWND ou la <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> méthode pour créer un environnement d’hébergement WPF. L’éditeur sous-jacent utilise toujours WPF, mais vous pouvez créer le type de volet de fenêtre adapté à vos besoins d’hébergement si vous incorporez ce volet de fenêtre directement dans votre propre contenu.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Utilisation des versions Win32 et WPF de IVsTextView  
 Vous pouvez définir en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> mode Win32 ou en mode WPF.  
  
 Lorsqu’une fabrique d’éditeur crée un affichage de texte, par défaut, il est hébergé dans un HWND et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> retourne un HWND. Vous ne devez pas utiliser ce mode pour incorporer l’éditeur à l’intérieur d’un contrôle WPF.  
  
 Pour définir l’affichage du texte en mode WPF, vous devez appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> et passer <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> comme l’un des indicateurs d’initialisation dans le `InitView` paramètre. Vous pouvez accéder <xref:System.Windows.FrameworkElement> à en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> .  
  
 Le mode WPF diffère du mode Win32 de deux manières. Tout d’abord, l’affichage de texte peut être hébergé dans un contexte WPF. Vous pouvez accéder au volet WPF en effectuant un cast <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> de en <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> et en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> . Deuxièmement, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> retourne toujours un HWND, mais ce HWND ne peut être utilisé que pour vérifier sa position et lui définir le focus. Vous ne devez pas utiliser ce HWND pour répondre à un message de WM_PAINT, car il n’affecte pas la manière dont l’éditeur peint la fenêtre. Ce HWND est présent uniquement pour faciliter la transition vers le nouveau code d’éditeur au moyen des adaptateurs. Il est vivement recommandé de ne pas utiliser `VIF_NO_HWND_SUPPORT` si votre composant requiert un HWND pour fonctionner, en raison des limitations du HWND renvoyé à partir de `GetWindowHandle` dans ce mode.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Passage de tableaux en tant que paramètres en code natif  
 Il existe de nombreuses méthodes dans l’API d’éditeur héritée qui ont des paramètres incluant un tableau et son nombre. Voici quelques exemples :  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Si vous appelez ces méthodes en code natif, vous devez passer un seul élément à la fois. Si vous transmettez plus d’un élément, l’appel est rejeté, en raison de problèmes liés à l’implémentation de l’interopérabilité principale.  
  
 Le problème est plus complexe avec des méthodes telles que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> . Chaque fois que cette méthode est appelée, elle efface la liste précédente de types de marqueurs ignorés. il n’est donc pas possible simplement d’appeler cette méthode trois fois avec trois types de marqueurs différents. La seule solution consiste à appeler cette méthode uniquement dans du code managé.  
  
#### <a name="threading"></a>Threads  
 Vous devez toujours appeler l’adaptateur de mémoire tampon à partir du thread d’interface utilisateur. L’adaptateur de mémoire tampon est un objet managé, ce qui signifie que son appel à partir du code managé contourne le marshaling COM et que votre appel ne sera pas automatiquement marshalé vers le thread d’interface utilisateur.  Si vous appelez l’adaptateur de mémoire tampon à partir d’un thread d’arrière-plan, vous devez utiliser <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ou une méthode similaire.  
  
#### <a name="lockbuffer-methods"></a>Méthodes LockBuffer  
 Toutes les méthodes LockBuffer () sont déconseillées. Voici quelques exemples :  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Événements de validation  
 Les événements de validation ne sont pas pris en charge. L’appel d’une méthode qui conseille pour ces événements fait que la méthode retourne un code d’échec.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 Le <xref:EnvDTE.TextEditorEvents> ne se déclenche plus sur la validation (). Au lieu de cela, ils se déclenchent à chaque modification de texte.  
  
#### <a name="text-markers"></a>Marqueurs de texte  
 Vous devez appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> les objets lorsque vous les supprimez. Dans les versions précédentes, vous deviez uniquement libérer les marqueurs.  
  
#### <a name="line-numbers"></a>Numéros de ligne  
 Pour diverses méthodes sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> et, les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> numéros de ligne correspondent aux numéros de ligne de mémoire tampon sous-jacents, et non aux numéros de ligne qui facteurnt le plan et le retour automatique à la ligne, comme dans Visual Studio 2008.  
  
 Les méthodes affectées sont les suivantes (la liste n’est pas exhaustive) :  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>mode Plan  
 Les clients de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> voient uniquement les régions en mode plan qui ont été ajoutées à l’aide <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> de ou de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> . Elles ne voient pas les régions ad hoc, car elles ne sont pas ajoutées par le biais des adaptateurs de l’éditeur. De même, ces clients ne verront pas les régions en mode plan ajoutées par les langages (y compris C# et C++) qui utilisent le nouveau code de l’éditeur plutôt que les adaptateurs de l’éditeur.  
  
#### <a name="line-heights"></a>Hauteurs de lignes  
 Dans le nouvel éditeur, les lignes de texte peuvent avoir des hauteurs différentes, en fonction de la taille de la police et des transformations de ligne possibles qui peuvent déplacer la ligne par rapport à d’autres lignes. La hauteur de ligne retournée par les méthodes telles que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> est la hauteur d’une ligne utilisant la taille de police par défaut sans transformations de ligne appliquée. Cette hauteur peut ou non refléter la hauteur réelle d’une ligne dans la vue.  
  
#### <a name="eventing-and-undo"></a>Événements et annulation  
 Dans le nouvel éditeur, la vue continue d’effectuer des opérations telles que le rendu et le déclenchement continus d’événements, même lorsqu’un cluster d’annulation est ouvert. Ce comportement est différent de celui des vues héritées, qui n’exécutaient pas ces opérations avant la fermeture du cluster d’annulation.  
  
#### <a name="intellisense"></a>IntelliSense  
  
- La <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> méthode échoue si vous transmettez une classe qui n’implémente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> ni ou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> . Les fenêtres contextuelles personnalisées owner-drawn ne sont plus prises en charge.  
  
#### <a name="smarttags"></a>SmartTag  
 Il n’existe aucune prise en charge d’adaptateur pour les balises actives créées avec les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData> interfaces,, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> .  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> n’est pas implémenté.  
  
## <a name="unimplemented-methods"></a>Méthodes non implémentées  
 Certaines méthodes n’ont pas été implémentées sur l’adaptateur de mémoire tampon de texte, l’adaptateur de vue de texte et l’adaptateur de couche de texte.  
  
|Interface|Non implémenté|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` n’est pas implémenté.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> est implémenté dans les adaptateurs mais ignoré par l’interface utilisateur du mode plan.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> est implémenté dans les adaptateurs mais ignoré par l’interface utilisateur du mode plan.|
