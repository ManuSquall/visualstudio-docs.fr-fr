---
title: "Comportement nouveau ou modifi&#233; avec les cartes d’&#233;diteur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "éditeurs (Visual Studio SDK), hérités : comportement de l’adaptateur"
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Comportement nouveau ou modifi&#233; avec les cartes d’&#233;diteur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous mettez à jour le code qui a été écrit avec des versions antérieures de l’éditeur principal de Visual Studio et que vous prévoyez d’utiliser l’éditeur adaptateurs \(ou shims\) au lieu d’utiliser la nouvelle API, vous devez connaître les différences suivantes dans le comportement des adaptateurs éditeur en ce qui concerne l’éditeur principal précédent.  
  
## Fonctionnalités  
  
#### À l’aide de la fonction SetSite\(\)  
 Vous devez appeler <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> lorsque vous CoCreate mémoires tampons de texte, les affichages de texte et de code windows avant d’effectuer d’autres opérations sur les. Toutefois, cela n’est pas nécessaire si vous utilisez le <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> pour les créer, car les méthodes de ce service Create\(\) s’appellent <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.  
  
#### Hébergement IVsCodeWindow et IVsTextView dans votre contenu  
 Vous pouvez héberger à la fois <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> dans votre contenu à l’aide en mode de Win32 ou WPF. Toutefois, gardez à l’esprit qu’il existe des différences dans les deux modes.  
  
##### À l’aide de versions de IVsCodeWindow Win32 et WPF  
 La fenêtre de l’éditeur de code est dérivée de <xref:Microsoft.VisualStudio.Shell.WindowPane>, qui implémente l’ancienne Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interface ainsi que le nouveau WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interface. Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> pour créer un environnement d’hébergement basée sur HWND, ou <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> pour créer un environnement d’hébergement WPF. L’éditeur sous\-jacente utilise toujours WPF, mais vous pouvez créer le type de volet de fenêtre adapté à vos exigences d’hébergement si vous incorporez ce volet directement dans votre propre contenu.  
  
##### À l’aide de versions de IVsTextView Win32 et WPF  
 Vous pouvez définir un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> au mode de Win32 ou WPF.  
  
 Lorsqu’une fabrique d’éditeur crée une vue de texte, par défaut, il est hébergé dans un HWND, et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> retourne un HWND. Vous ne devez pas utiliser ce mode incorporer l’éditeur à l’intérieur d’un contrôle WPF.  
  
 Pour définir une vue de texte en mode de WPF, vous devez appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> et transmettre <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> comme indicateurs d’un de l’initialisation de le `InitView` paramètre. Vous pouvez obtenir le <xref:System.Windows.FrameworkElement> en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.  
  
 Le mode WPF est différent du mode Win32 de deux manières. Tout d’abord, l’affichage de texte peut être hébergé dans un contexte WPF. Vous pouvez accéder au volet WPF en convertissant le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> à <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> et en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Ensuite, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> toujours retourne un HWND, mais ce HWND peut servir uniquement à vérifier sa position et définir le focus sur celui\-ci. Vous ne devez pas utiliser ce HWND pour répondre à un message WM\_PAINT, parce que cela n’affecte pas la façon dont l’éditeur peint la fenêtre. Ce HWND est présent uniquement à faciliter la transition vers le nouveau code de l’éditeur au moyen de cartes. Il est fortement recommandé que vous ne devez pas utiliser `VIF_NO_HWND_SUPPORT` Si votre composant requiert un HWND travailler, en raison des limitations dans le HWND retourné à partir de `GetWindowHandle` alors que dans ce mode.  
  
#### Passage de tableaux en tant que paramètres dans le code natif  
 Il existe de nombreuses méthodes dans le API héritées de l’éditeur qui ont des paramètres qui incluent un tableau et son décompte. Les exemples sont :  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Si vous appelez ces méthodes en code natif, vous devez passer un seul élément à la fois. Si vous passez plusieurs éléments, l’appel rejeté en raison de problèmes avec l’implémentation d’interopérabilité primaire.  
  
 Le problème est plus complexe avec des méthodes telles que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Chaque fois que cette méthode est appelée, elle efface la liste précédente des types de marqueur ignorés, donc il n’est pas possible de simplement appeler cette méthode trois fois avec trois types différents de marqueur. La seule solution consiste à appeler cette méthode uniquement dans le code managé.  
  
#### Thread  
 Vous devez toujours appeler l’adaptateur de la mémoire tampon à partir du thread d’interface utilisateur. L’adaptateur de la mémoire tampon est un objet géré, ce qui signifie qu’appeler dans celui\-ci à partir de code managé ignore le marshaling COM et votre appel n'est pas automatiquement marshalé au thread d’interface utilisateur.  Si vous appelez l’adaptateur de la mémoire tampon à partir d’un thread d’arrière\-plan, vous devez utiliser <xref:System.Windows.Threading.Dispatcher.Invoke%2A> ou une méthode similaire.  
  
#### Méthodes LockBuffer  
 Toutes les méthodes LockBuffer\(\) sont déconseillés. Les exemples sont :  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### Événements de validation  
 Valider les événements ne sont pas pris en charge. Appel d’une méthode qui recommande de ces événements indique à la méthode retourner un code d’échec.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### TextEditorEvents  
 Le <xref:EnvDTE.TextEditorEvents> ne se déclenchent pas sur Commit\(\). Au lieu de cela, ils sont déclenchés à chaque modification de texte.  
  
#### Marqueurs de texte  
 Vous devez appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> objets lorsque vous les supprimez. Dans les versions précédentes, vous deviez uniquement les indicateurs de version.  
  
#### Numéros de ligne  
 Un ensemble de méthodes sur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, pas numéros de ligne que le facteur de délimitation et de retour, comme dans Visual Studio 2008, les numéros de ligne correspondent aux numéros de ligne de mémoire tampon sous\-jacente.  
  
 Les méthodes affectées sont les suivantes \(la liste n’est pas exhaustive\) :  
  
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
  
#### Mode Plan  
 Les clients de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> s’affiche uniquement dans les régions en mode plan qui ont été ajoutées à l’aide de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>ou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Ils verront pas les zones appropriées, car ils ne sont pas ajoutés via l’éditeur de cartes. De même, ces clients ne verront pas ajoutées par les langages \(y compris c\# et C\+\+\) qui utilisent le nouveau code de l’éditeur, plutôt que les adaptateurs d’éditeur de régions en mode plan.  
  
#### Hauteur des lignes  
 Dans le nouvel éditeur de lignes de texte peuvent avoir des hauteurs différentes, selon la taille de police et les transformations de ligne possible qui peuvent passer à la ligne par rapport à d’autres lignes. La hauteur des lignes retournée par les méthodes telles que <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> correspond à la hauteur d’une ligne avec aucune ligne les transformations appliquées à l’aide de la taille de police par défaut. Cette hauteur peut ou peut ne pas refléter la hauteur réelle d’une ligne dans la vue.  
  
#### Gestion des événements et annulation  
 Dans le nouvel éditeur, la vue continue à effectuer des opérations de rendu et de déclencher des événements en permanence, même lorsqu’un cluster d’annulation n’est ouvert. Ce comportement est différent de celui de vues hérités, ce qui n’a pas effectué ces opérations qu’après la fermeture du cluster Annuler.  
  
#### IntelliSense  
  
-   Le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> méthode échoue si vous passez dans une classe qui n’implémente pas <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> ou <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Les messages owner\-drawn personnalisés Win32 ne sont plus pris en charge.  
  
#### Balises actives  
 Il n’existe aucune prise en charge de l’adaptateur pour les balises actives, créée avec <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, et <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> interfaces.  
  
#### DTE  
 <xref:EnvDTE80.IncrementalSearch> n’est pas implémentée.  
  
## Méthodes non implémentées  
 Certaines méthodes n’ont pas été implémentées sur la carte de mémoire tampon de texte, adaptateur de vue de texte et carte de couche de texte.  
  
|Interface|Non implémenté|  
|---------------|--------------------|  
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