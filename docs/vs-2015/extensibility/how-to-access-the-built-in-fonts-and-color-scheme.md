---
title: 'Comment : accéder aux polices et au modèle de couleurs intégrés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685307"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Guide pratique pour accéder aux polices intégrées et au modèle de couleurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’environnement de développement intégré (IDE) de Visual Studio dispose d’un schéma de polices et de couleurs associées à la fenêtre de l’éditeur. Vous pouvez accéder à ce schéma par le biais de l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.  
  
 Pour utiliser le modèle de polices et de couleurs intégré, un VSPackage doit :  
  
- Définissez une catégorie à utiliser avec le service polices et couleurs par défaut.  
  
- Inscrivez la catégorie avec le serveur de polices et de couleurs par défaut.  
  
- Conseillez à l’IDE qu’une fenêtre spécifique utilise les éléments et les catégories d’affichage intégrés à l’aide des `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfaces et.  
  
  L’IDE utilise la catégorie résultante comme handle de la fenêtre. Le nom de la catégorie est affiché dans la zone de liste déroulante **afficher les paramètres de :** de la page de propriétés **polices et couleurs** .  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Pour définir une catégorie à l’aide de couleurs et de polices intégrées  
  
1. Créez un GUID arbitraire.  
  
    Ce GUID est utilisé pour identifier une catégorie de manière unique<strong>.</strong> Cette catégorie réutilise la spécification des polices et couleurs par défaut de l’IDE.  
  
   > [!NOTE]
   > Lorsque vous récupérez des données de police et de couleur avec le <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> ou d’autres interfaces, les VSPackages utilisent ce GUID pour référencer les informations intégrées.  
  
2. Le nom de la catégorie doit être ajouté à une table de chaînes à l’intérieur du fichier de ressources (. RC) du VSPackage, afin qu’il puisse être localisé en fonction des besoins lorsqu’il est affiché dans l’IDE.  
  
    Pour plus d’informations, consultez [Ajout ou suppression d’une chaîne](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Pour inscrire une catégorie à l’aide des couleurs et des polices intégrées  
  
1. Construisez un type spécial d’entrée de Registre Category à l’emplacement suivant :  
  
     [Hklm\software\microsoft. \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<Category>* ]  
  
     *\<Category>* est le nom non localisé de la catégorie.  
  
2. Renseignez le registre pour utiliser les polices et le modèle de couleurs de stock avec quatre valeurs :  
  
    |Nom|Type|Données|Description|  
    |----------|----------|----------|-----------------|  
    |Category|REG_SZ|GUID|GUID arbitraire qui identifie une catégorie qui contient la police et le modèle de couleurs de l’action.|  
    |Package|REG_SZ|GUID|F5E7E71D-1401-11D1-883B-0000F87579D2<br /><br /> Ce GUID est utilisé par tous les VSPackages qui utilisent les configurations de police et de couleur par défaut.|  
    |NameID|REG_DWORD|ID|ID de ressource d’un nom de catégorie localisable dans le VSPackage.|  
    |ToolWindowPackage|REG_SZ|GUID|GUID du VSPackage qui implémente l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Pour initier l’utilisation des polices et des couleurs fournies par le système  
  
1. Créez une instance de l' `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interface dans le cadre de l’implémentation et de l’initialisation de la fenêtre.  
  
2. Appelez la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> méthode pour obtenir une instance de l' `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interface correspondant à l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> instance actuelle.  
  
3. Appelez <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> deux fois.  
  
   - Appelez une fois avec `VSEDITPROPID_ViewGeneral_ColorCategory` comme argument.  
  
   - Appelez une fois avec `VSEDITPROPID_ViewGeneral_FontCategory` comme argument.  
  
     Cela définit et expose les services polices et couleurs par défaut en tant que propriété de la fenêtre.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de polices et de couleurs intégrées.  
  
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
 [Utilisation des polices et des couleurs](../extensibility/using-fonts-and-colors.md)   
 [Obtention d’informations sur la police et la couleur pour la coloration du texte](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Accès aux paramètres de police et de couleur stockés](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Présentation de la couleur et de la police](../extensibility/font-and-color-overview.md)
