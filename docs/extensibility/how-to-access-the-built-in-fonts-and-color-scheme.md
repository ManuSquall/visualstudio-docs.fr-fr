---
title: "Comment&#160;: acc&#233;der aux polices int&#233;gr&#233;es et jeu de couleurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "polices, l’accès à intégré"
  - "police et couleur de contrôle (Visual Studio SDK), catégories"
  - "couleurs, l’accès aux schémas intégrés"
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: acc&#233;der aux polices int&#233;gr&#233;es et jeu de couleurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L’environnement de développement intégré \(IDE\) Visual Studio possède un jeu de polices et couleurs qui est associé à la fenêtre de l’éditeur. Vous pouvez accéder à ce schéma via les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.  
  
 Pour utiliser les polices intégrées et le jeu de couleurs, un VSPackage doit :  
  
-   Définir une catégorie à utiliser avec le service de polices et les couleurs par défaut.  
  
-   Enregistrer la catégorie avec le serveur de polices et les couleurs par défaut.  
  
-   Informer l’IDE qu’une fenêtre spécifique utilise les catégories et les éléments d’affichage intégré à l’aide de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` et `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfaces.  
  
 L’IDE utilise la catégorie résultant comme un handle vers la fenêtre. Nom de la catégorie s’affiche dans le **Afficher les paramètres de :** zone de liste déroulante dans le **polices et couleurs** page de propriétés.  
  
### Pour définir une catégorie à l’aide de couleurs et polices intégrées  
  
1.  Créer un GUID arbitraire.  
  
     Ce GUID est utilisé pour identifier de manière unique une catégorie**.** Cette catégorie réutilise les polices par défaut de l’IDE et la spécification de couleurs.  
  
    > [!NOTE]
    >  Lors de la récupération des données de police et couleur avec la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> ou d’autres interfaces, les VSPackages utiliser ce GUID pour référencer des informations intégrées.  
  
2.  Nom de la catégorie doit être ajouté à une table de chaînes à l’intérieur du fichier de ressources \(.rc\) du VSPackage, afin qu’elle peut être localisée en fonction des besoins lors de l’affiche dans l’IDE.  
  
     Pour plus d'informations, consultez [Adding or Deleting a String](/visual-cpp/windows/adding-or-deleting-a-string).  
  
### Pour inscrire une catégorie à l’aide de couleurs et polices intégrées  
  
1.  Construire un type spécial d’entrée de Registre de catégorie dans l’emplacement suivant :  
  
     \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\*\< version de Visual Studio \>*\\FontAndColors\\*\< catégorie \>*\]  
  
     *\< catégorie \>* est le nom non localisé de la catégorie.  
  
2.  Remplir le Registre pour utiliser le jeu de couleurs et de polices du stock avec quatre valeurs :  
  
    |Nom|Type|Données|Description|  
    |---------|----------|-------------|-----------------|  
    |Catégorie|REG\_SZ|GUID|Un GUID arbitraire qui identifie une catégorie qui contient le jeu de couleurs et de polices stock.|  
    |Package|REG\_SZ|GUID|{F5E7E71D\-1401\-11D1\-883B\-0000F87579D2}<br /><br /> Ce GUID est utilisé par tous les packages VS qui utilisent les configurations de police et la couleur par défaut.|  
    |NameID|REG\_DWORD|ID|L’ID de ressource d’un nom de catégorie localisables dans le VSPackage.|  
    |ToolWindowPackage|REG\_SZ|GUID|Le GUID de l’implémentation VSPackage le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.|  
  
3.  
  
### Pour lancer l’utilisation des couleurs et polices fournies par le système  
  
1.  Créez une instance de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interface dans le cadre de l’implémentation et de l’initialisation de la fenêtre.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> méthode pour obtenir une instance de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interface correspondant à l’actuel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> instance.  
  
3.  Appeler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> deux fois.  
  
    -   Appeler une fois avec `VSEDITPROPID_ViewGeneral_ColorCategory`en tant qu’argument.  
  
    -   Appeler une fois avec `VSEDITPROPID_ViewGeneral_FontCategory` en tant qu’argument.  
  
     Cela définit et expose les services de polices et les couleurs par défaut en tant que propriété de la fenêtre.  
  
## Exemple  
 L’exemple suivant initialise l’utilisation des couleurs et polices intégrées.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## Voir aussi  
 [Utilisation de polices et couleurs](../extensibility/using-fonts-and-colors.md)   
 [Mise en route de la police et les informations de couleur de colorisation de texte](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [L'accès à stockée paramètres de police et couleur](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Vue d'ensemble de la couleur et de police](../extensibility/font-and-color-overview.md)