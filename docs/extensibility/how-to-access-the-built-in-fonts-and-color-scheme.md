---
title: "Comment : accéder au jeu de couleurs et polices intégrées | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: f646bb0a1606bd5944c945c5db89083fa265afbd
ms.contentlocale: fr-fr
ms.lasthandoff: 04/05/2017

---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Comment : accéder aux polices intégrées et jeu de couleurs
L’environnement de développement intégré (IDE) Visual Studio a un jeu de polices et couleurs qui est associé à la fenêtre de l’éditeur. Vous pouvez accéder à ce schéma via les <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>  
  
 Pour utiliser les polices intégrées et un jeu de couleurs, un VSPackage doit :  
  
-   Définir une catégorie à utiliser avec le service de polices et couleurs par défaut.  
  
-   Enregistrer la catégorie avec le serveur de polices et couleurs par défaut.  
  
-   Informez l’IDE qu’une fenêtre spécifique utilise les catégories et les éléments d’affichage intégré à l’aide de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` et `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfaces.  
  
 L’IDE utilise la catégorie résultante en tant qu’un handle de fenêtre. Nom de la catégorie s’affiche dans le **afficher les paramètres de :** zone de liste déroulante dans le **polices et couleurs** page de propriétés.  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Pour définir une catégorie à l’aide de couleurs et polices intégrées  
  
1.  Créer un GUID arbitraire.  
  
     Ce GUID est utilisé pour identifier de manière unique une catégorie**.** Cette catégorie réutilise la spécification de couleurs et de polices par défaut de l’IDE.  
  
    > [!NOTE]
    >  Lors de la récupération des données de police et couleur avec la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>ou d’autres interfaces, VSPackages utilisent ce GUID pour référencer les informations intégrées.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
2.  Nom de la catégorie doit être ajouté à une table de chaînes à l’intérieur du fichier de ressources (.rc) le VSPackage, afin qu’elle peut être localisée en fonction des besoins lorsque affichés dans l’IDE.  
  
     Pour plus d’informations, consultez [Ajout ou suppression d’une chaîne](/cpp/windows/adding-or-deleting-a-string).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Pour inscrire une catégorie à l’aide de couleurs et polices intégrées  
  
1.  Construire un type spécial de l’entrée de Registre de catégorie dans l’emplacement suivant :  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<version de Visual Studio >*\FontAndColors\\*\<catégorie >*]  
  
     *\<Catégorie >* est le nom non localisé de la catégorie.  
  
2.  Remplir le Registre pour utiliser le jeu de couleurs et polices du stock de quatre valeurs :  
  
    |Nom|Type|Données|Description|  
    |----------|----------|----------|-----------------|  
    |Catégorie|REG_SZ|GUID|Un GUID arbitraire qui identifie une catégorie qui contient le schéma de police et couleur de stock.|  
    |Package|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Ce GUID est utilisé par tous les packages VS qui utilisent les configurations de police et la couleur par défaut.|  
    |NameID|REG_DWORD|Id|L’ID de ressource de nom de la catégorie localisables dans le VSPackage.|  
    |ToolWindowPackage|REG_SZ|GUID|Le GUID du VSPackage qui implémente le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>interface.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
  
3.  
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Pour lancer l’utilisation de couleurs et polices fournies par le système  
  
1.  Créez une instance de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interface dans le cadre de l’implémentation et l’initialisation de la fenêtre.  
  
2.  Appelez le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>méthode pour obtenir une instance de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interface correspondant à actuel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>instance.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>  
  
3.  Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>à deux reprises.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>  
  
    -   Appeler une fois avec `VSEDITPROPID_ViewGeneral_ColorCategory`en tant qu’argument.  
  
    -   Appeler une fois avec `VSEDITPROPID_ViewGeneral_FontCategory` en tant qu’argument.  
  
     Cela définit et expose les services de polices et couleurs par défaut en tant que propriété de la fenêtre.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant démarre l’utilisation de couleurs et polices intégrées.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des polices et couleurs](../extensibility/using-fonts-and-colors.md)   
 [Mise en route de la police et les informations de couleur de colorisation de texte](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [L’accès à la police stockée et les paramètres de couleur](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Vue d’ensemble de la couleur et de police](../extensibility/font-and-color-overview.md)
