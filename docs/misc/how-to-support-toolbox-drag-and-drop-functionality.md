---
title: "Comment&#160;: prendre en charge la fonctionnalit&#233; glisser-d&#233;placer de la bo&#238;te &#224; outils | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "glisser-déplacer, prise en charge dans la boîte à outils"
  - "Boîte à outils (SDK Visual Studio), client"
  - "Boîte à outils (SDK Visual Studio), glisser-déplacer"
ms.assetid: 2f73a03c-1eb1-4b88-9c1b-d63ba0e2ac90
caps.latest.revision: 18
caps.handback.revision: 18
manager: "douge"
---
# Comment&#160;: prendre en charge la fonctionnalit&#233; glisser-d&#233;placer de la bo&#238;te &#224; outils
> [!NOTE]
>  Pour ajouter des contrôles personnalisés à la boîte à outils, il est recommandé d’utiliser les modèles de contrôles de boîte à outils fournis avec le Kit de développement logiciel \(SDK\) Visual Studio 10, celui\-ci intégrant la prise en charge de la fonctionnalité glisser\-déplacer. Cette rubrique est uniquement conservée pour assurer la compatibilité descendante et permettre l’utilisation des contrôles existants.  
>   
>  Pour plus d’informations sur la création de contrôles de boîte à outils à l’aide de modèles, consultez [Comment : créer un contrôle de boîte à outils qui utilise Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md) et [Création d’un contrôle de boîte à outils WPF](../extensibility/creating-a-wpf-toolbox-control.md).  
  
 Les VSPackages doivent implémenter la prise en charge de la fonctionnalité glisser\-déplacer pour utiliser les contrôles **Boîte à outils** sur les vues de document, comme les éditeurs ou les concepteurs.  
  
 Par défaut, tous les objets [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dérivés de <xref:System.Windows.Forms.Control?displayProperty=fullName> prennent en charge de manière automatique et transparente la consommation des contrôles **Boîte à outils**. Les procédures décrites ci\-dessous sont donc inutiles. Vous pouvez étendre les fonctionnalités de base en créant un concepteur.  
  
 Pour plus d’informations, consultez [Vue d'ensemble des Windows Forms](../Topic/Windows%20Forms%20Overview.md) et [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md).  
  
### Pour implémenter la fonctionnalité glisser\-déplacer de base  
  
1.  Assurez la prise en charge de la fonctionnalité glisser\-déplacer en implémentant <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> sur un objet de vue. La vue bénéficie ainsi de la fonctionnalité glisser\-déplacer OLE et de la sérialisation du contrôle.  
  
     Pour plus d’informations sur l’implémentation de la fonctionnalité glisser\-déplacer, consultez [Glisser\-déplacer \(OLE\)](/visual-cpp/mfc/drag-and-drop-ole).  
  
     Vous pouvez déplacer des éléments du Presse\-papiers ou des contrôles sur un concepteur. Pour plus d’informations sur les formats de Presse\-papiers standard pris en charge par la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Boîte à outils**, consultez [Extension de la boîte à outils](../misc/extending-the-toolbox.md).  
  
2.  Mettez en œuvre une implémentation de base de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> sur une vue de document.  
  
     Quand un utilisateur tente de faire glisser un contrôle de boîte à outils sur une vue, le shell [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interroge le VSPackage de la vue pour déterminer s’il implémente l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>.  
  
    1.  Implémentez <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A> de manière à retourner <xref:Microsoft.VisualStudio.VSConstants.S_OK> pour les formats **Boîte à outils** pris en charge par la cible de déplacement. L’exemple suivant vérifie si l’objet de données est au format de Presse\-papiers personnalisé \(`CF_CUSTOM_FORMAT`\) et s’il s’agit d’un contrôle ActiveX.  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::IsSupported(IDataObject* pDO) { HRESULT hr; STGMEDIUM stm; if (!pDO) return E_POINTER; // Determine if the data object is in the Custom clip board format // fetc is the dialog editor toolbox item template. FORMATETC fetc = { m_CF_CUSTOM_FORMAT, //Value set with RegisterClipboardFormat NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (FAILED(hr = pDO->GetData(&fetc, &stm))) { // Determine if the object is in the class-id clipboard format ... this // would be the case if the control is an activeX toolbox item. FORMATETC xfetc = { m_CF_CLSID, NULL, DVASPECT_CONTENT, // DVASCPECT_ICON might be better -1, TYMED_HGLOBAL }; if (SUCCEEDED(hr = pDO->GetData(&xfetc,&stm))) { USES_CONVERSION; GUID guid; LPSTR pData = (LPSTR)GlobalLock(stm.hGlobal); if (pData) { // Convert from the string format to a binary GUID. if (CLSIDFromString(A2W(pData), &guid) != S_OK) return E_FAIL; // HTML data objects could have CLSID format ... so any data object could // be returned as a NULL guid ... fail on null guid, obviously they are // not active X controls. if (guid == GUID_NULL) return E_FAIL; } } } return hr; }  
        ```  
  
         L’IDE vérifie ces informations la première fois qu’une fenêtre de vue est chargée et chaque fois que cette fenêtre est activée quand un utilisateur réinitialise la **Boîte à outils** par le biais de la boîte de dialogue **Personnaliserla boîte à outils** de l’IDE. En règle générale, la **Boîte à outils** n’affiche pas les éléments **Boîte à outils** non pris en charge.  
  
         Les utilisateurs peuvent définir une option pour afficher en permanence toutes les pages Boîte à outils. Dans ce cas, l’environnement n’interroge pas l’éditeur concernant <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.IsSupported%2A>.  
  
    2.  Quand une implémentation de <xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget> \(telle que celle décrite ci\-dessus\) gère correctement un composant déplacé, l’objet de vue doit le signaler à l’environnement [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.DataUsed%2A>.  
  
     Si vous le souhaitez, vous pouvez étendre la prise en charge de la fonctionnalité glisser\-déplacer d’un VSPackage en étendant son implémentation <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>.  
  
3.  Une implémentation <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> peut aussi prendre en charge le déplacement d’éléments **Boîte à outils** sur une fenêtre par sélection \(plutôt qu’à la suite d’une action de la souris\). Autrement dit, un utilisateur peut faire glisser un élément soit en double\-cliquant sur un élément **Boîte à outils**, soit en effectuant un clic simple et en appuyant sur Entrée. Pour ce faire :  
  
    1.  Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A>.  
  
         Cette méthode, appelée par l’IDE, est sélectionnée quand l’utilisateur effectue un clic ou appuie sur Entrée.  
  
         La méthode doit insérer l’élément **Boîte à outils** dans la fenêtre cible.  
  
    2.  Si vous ne souhaitez pas prendre en charge l’implémentation par sélection, la méthode doit retourner <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>.  
  
         Dans l’exemple ci\-dessous, l’implémentation de la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser.ItemPicked%2A> vérifie si l’objet sélectionné est pris en charge et, le cas échéant, le désérialise dans le code :  
  
        ```cpp#  
        STDMETHODIMP CustTbxUser::ItemPicked(IDataObject* pDataObject) { if (!pDataObject) return E_POINTER; UINT nIDTool; if (IsSupported(pDataObject) == S_OK) { SetToolCursor(); m_pDataObject = pDataObject; nIDTool = DeserializeObject(); // Get the focus back m_pResObject->m_spWndFrame->Show(); return S_OK; } }  
        ```  
  
4.  Effectuez les étapes suivantes pour veiller au maintien du focus approprié pour votre application :  
  
    1.  Si votre fenêtre d’éditeur implémente deux volets différents, et non deux vues différentes, appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2.UpdateToolboxUI%2A> quand vous passez d’un volet actif à un autre dans votre fenêtre d’éditeur. Vous savez alors quand les modifications d’activation se produisent dans votre fenêtre.  
  
    2.  Pour activer correctement la fenêtre et vous assurer que le routage de commande est correctement mis à jour, vous devez appeler la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> sur le composant. Cette action doit être prise quand vous affectez le focus à une fenêtre de composant, comme un éditeur, qui a été créée ou modifiée par une opération de glisser\-déplacer impliquant la boîte à outils.  
  
 Un VSPackage peut intervenir dans une opération de glissement et modifier l’élément déplacé par le biais de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>.  
  
 Par exemple, au lieu d’ajouter explicitement un nouveau contrôle **Boîte à outils** à la **Boîte à outils**, un VSPackage peut intercepter une **Boîte à outils** standard au moment du déplacement et la remplacer par une implémentation personnalisée.  
  
### Pour modifier dynamiquement des contrôles de boîte à outils  
  
1.  Implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>.  
  
     Chaque fois qu’un élément **Boîte à outils** fait l’objet d’une sélection ou d’un déplacement, la **Boîte à outils** interroge la cible de déplacement pour déterminer si elle prend en charge l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook>. Dans l’affirmative, elle appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A>.  
  
2.  La méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxActiveUserHook.InterceptDataObject%2A> doit retourner un nouvel objet <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject> à utiliser au lieu du <xref:Microsoft.VisualStudio.OLE.Interop.IDataObject> d’origine.  
  
     Si la cible de déplacement n’a pas besoin de se substituer à l’objet de données, elle doit retourner son entrée.  
  
 Un VSPackage peut autoriser les utilisateurs à appuyer sur Ctrl\+Maj\+V pour parcourir le contenu du Presse\-papiers.  
  
### Pour prendre en charge un Presse\-papiers circulaire  
  
1.  Implémentez un gestionnaire pour la commande `CMDIDPasteNextTBXCBItem` à l’aide des éléments suivants :  
  
    -   <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> pour les VSPackages basés sur un assembly d’interopérabilité ;  
  
    -   <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> pour les VSPackages basés sur MPF \(Managed Package Framework\) ; l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler>.  
  
2.  Dans le gestionnaire de commandes, implémentez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.AreDataObjectsAvailable%2A> pour déterminer s’il existe des objets du Presse\-papiers à parcourir.  
  
    1.  Si aucun élément ne figure dans le Presse\-papiers de la boîte à outils, l’environnement vérifie alors le Presse\-papiers du système pour voir si celui\-ci contient des éléments.  
  
    2.  Si des éléments figurent dans le Presse\-papiers du système, mais pas dans le Presse\-papiers de la boîte à outils, le Presse\-papiers circulaire est rempli avec les éléments du système.  
  
    3.  Pour sélectionner le prochain élément dans la liste, l’implémentation appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.GetAndSelectNextDataObject%2A>.  
  
    4.  Pour retourner au début du cycle du Presse\-papiers, appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxClipboardCycler.BeginCycle%2A>.  
  
## Voir aussi  
 [Extension de la boîte à outils](../misc/extending-the-toolbox.md)   
 [Comment : fournir des éléments de boîte à outils personnalisés à l’aide d’assemblys d’interopérabilité](../Topic/How%20to:%20Provide%20Custom%20Toolbox%20Items%20By%20Using%20Interop%20Assemblies.md)   
 [Développement avancé de contrôles de boîte à outils](/visual-cpp/misc/advanced-toolbox-control-development)   
 [Inscription des fonctionnalités de prise en charge de boîte à outils](../misc/registering-toolbox-support-features.md)   
 [Gestion de la boîte à outils](/visual-cpp/misc/managing-the-toolbox)