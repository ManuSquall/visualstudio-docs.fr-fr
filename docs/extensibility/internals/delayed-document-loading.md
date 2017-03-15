---
title: "Document chargement diff&#233;r&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Document chargement diff&#233;r&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lorsqu'un utilisateur rouvre une solution Visual Studio, la plupart des documents associés n'est pas chargée immédiatement. Le cadre de la fenêtre de document est créé dans un état en attente d'initialisation et un espace réservé \(appelé un frame de stub\) est placé dans la Table de Document en cours d'exécution \(r & DT\).  
  
 Votre extension peut provoquer des documents du projet à charger inutilement en interrogeant les éléments dans les documents avant leur chargement. Cela peut augmenter l'encombrement mémoire de Visual Studio.  
  
## Chargement de documents  
 Le document et le frame de stub sont entièrement initialisés lorsque l'utilisateur accède au document, par exemple en sélectionnant l'onglet de la fenêtre frame. Le document peut également être initialisé par une extension qui demande des données du document, soit en accédant à la r & DT directement pour acquérir les données du document, ou accéder à la r & DT indirectement en définissant un des appels suivants :  
  
-   Le frame de fenêtre Afficher la méthode : <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
-   Le frame de fenêtre méthode GetProperty <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> sur l'une des propriétés suivantes :  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
    -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
 Si votre extension utilise du code managé, vous ne devez pas appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> sauf si vous êtes certain que le document n'est pas dans l'état en attente d'initialisation, ou vous souhaitez que le document soit entièrement initialisé... Il s'agit, car cette méthode retourne toujours le document objet de données, créant si nécessaire. Au lieu de cela, vous devez appeler une des méthodes sur l'interface IVsRunningDocumentTable4.  
  
 Si votre extension utilise C\+\+, vous pouvez passer `null` pour les paramètres que vous ne souhaitez pas.  
  
 Vous pouvez éviter le chargement de documents inutiles en appelant une des méthodes suivantes avant de vous demander les propriétés pertinentes : avant de demander à d'autres propriétés.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> à l'aide de <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Cette méthode retourne un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> objet qui inclut une valeur pour <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Si le document n'a pas encore été initialisé.  
  
 Vous pouvez déterminer à quel moment un document a été chargé en vous abonnant à l'événement de r & DT qui est déclenché lorsqu'un document est entièrement initialisé. Il existe deux possibilités :  
  
-   Si le récepteur d'événements implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, vous pouvez vous abonner à <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
-   Sinon, vous pouvez vous abonner à <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
 Voici un scénario d'accès aux documents hypothétique. Visual Studio extension souhaitez afficher des informations sur les documents ouverts, par exemple la modification verrouiller count et des informations sur les données du document. Il énumère les documents dans l'utilisation de r & DT <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, puis appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> pour chaque document afin de récupérer les données de verrouillage modifier nombre et de document. Si le document est dans l'état en attente d'initialisation, qui demande les données de document entraîne à initialiser inutilement.  
  
 Un moyen plus efficace de cette opération consiste à utiliser <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> pour obtenir le nombre de verrous de modification, puis utilisez <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> pour déterminer si le document a été initialisé. Si les indicateurs n'incluent pas <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, le document a déjà été initialisé et demande les données de document avec <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> n'entraîne pas de toute initialisation inutile. Si les indicateurs incluent <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, l'extension doit éviter de demander les données du document jusqu'à ce que le document est initialisé. Cela peut être détecté dans le Gestionnaire d'événements OnAfterAttributeChange\(Ex\).  
  
## Extensions pour voir si elles force l'initialisation de test  
 Il n'existe aucune indication visible pour indiquer si un document a été initialisé, donc il peut être difficile de savoir si votre extension est forçant. Vous pouvez définir une clé de Registre qui facilite la vérification, car elle force le titre de tous les documents qui ne sont pas complètement initialisé pour que le texte `[Stub]` dans le titre.  
  
 Dans **HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0\\BackgroundSolutionLoad\]**, définissez **StubTabTitleFormatString** à **{0} \[Stub\]**.