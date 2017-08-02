---
title: "Guide pratique pour créer et appliquer une ressource | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: fb1bcd92e8f7bda12e774b969da2c71dfc38ab2f
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-create-and-apply-a-resource"></a>Guide pratique pour créer et appliquer une ressource
Les styles et les modèles des éléments du concepteur XAML sont stockés dans des entités réutilisables appelées ressources. Les styles vous permettent de définir les propriétés des éléments et de réutiliser ces paramètres pour que l'apparence des différents éléments demeure cohérente. Un [ControlTemplate](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.aspx) définit l’apparence d’un contrôle et peut également être appliqué en tant que ressource. Pour plus d’informations, consultez [Démarrage rapide : contrôles de styles](http://go.microsoft.com/fwlink/?LinkID=248239) et [Démarrage rapide : modèles de contrôles](http://go.microsoft.com/fwlink/?LinkID=247982).  
  
 Quand vous créez une ressource à partir d’une propriété existante, [Style](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx) ou `ControlTemplate`, la boîte de dialogue **Créer une ressource** vous permet de définir la ressource au niveau de l’application, du document ou de l’élément. Ces niveaux déterminent où vous pouvez utiliser la ressource. Par exemple, si vous définissez la ressource au niveau de l'élément, elle peut être appliquée uniquement à l'élément sur lequel vous l'avez créée. Vous pouvez également choisir de stocker la ressource dans un dictionnaire de ressources. Il s'agit d'un fichier distinct que vous pouvez réutiliser dans un autre projet.  
  
### <a name="to-create-a-new-resource"></a>Pour créer une ressource  
  
1.  Après avoir ouvert un fichier XAML dans le concepteur XAML, créez un élément ou choisissez un élément dans la fenêtre Structure du document.  
  
2.  Dans la fenêtre Propriétés, choisissez le marqueur de propriété, qui apparaît sous la forme d’un symbole de boîte à droite d’une valeur de propriété, puis choisissez **Convertir en nouvelle ressource**. Un symbole de zone blanche indique une valeur par défaut, tandis qu'un symbole de zone noire indique généralement qu'une ressource locale a été appliquée.  
  
     La boîte de dialogue appropriée pour la création d'une ressource s'affiche. Cette boîte de dialogue apparaît quand vous créez une ressource à partir d'un pinceau :  
  
     ![Boîte de dialogue Créer une ressource](~/docs/designers/media/xaml_create_resource.png "xaml_create_resource")  
  
3.  Dans la zone **Nom (Clé)**, entrez un nom de clé. C'est le nom que vous pouvez utiliser pour que d'autres éléments fassent référence à la ressource.  
  
4.  Sous **Définir dans**, choisissez l’option qui spécifie où vous voulez définir la ressource :  
  
    -   Pour que la ressource soit disponible pour n’importe quel document dans votre application, choisissez **Application**.  
  
    -   Pour qu’elle soit disponible seulement pour le document actif, choisissez **Ce document**.  
  
    -   Pour qu’elle soit disponible seulement pour l’élément à partir duquel vous l’avez créée ou pour ses éléments enfants, choisissez **Ce document** puis, dans la liste déroulante, sélectionnez *élément*:*nom*.  
  
    -   Pour définir la ressource dans un fichier de dictionnaire de ressources réutilisable dans d’autres projets, cliquez sur **Dictionnaire de ressources** puis sélectionnez un fichier de dictionnaire de ressources existant dans la liste déroulante, comme **StandardStyles.xaml**.  
  
5.  Choisissez le bouton **OK** pour créer la ressource et l’appliquer à l’élément à partir duquel vous l’avez créée.  
  
### <a name="to-apply-a-resource-to-an-element-or-property"></a>Pour appliquer une ressource à un élément ou à une propriété  
  
1.  Dans la fenêtre Structure du document, choisissez l'élément auquel vous souhaitez appliquer une ressource.  
  
2.  Effectuez l’une des opérations suivantes :  
  
    -   Appliquer une ressource à une propriété. Dans la fenêtre Propriétés, cliquez sur le marqueur de propriété en regard de la valeur de propriété, choisissez **Ressource locale** ou **Ressource système**, puis sélectionnez une ressource disponible dans la liste qui apparaît.  
  
         L’absence d’une ressource peut s’expliquer par le fait que son type ne correspond pas au type de la propriété.  
  
    -   Appliquer une ressource de modèle de style ou de contrôle à un contrôle. Ouvrez le menu contextuel d’un contrôle dans la fenêtre Structure du document, choisissez **Modifier un modèle** ou **Modifier d’autres modèles**, **Appliquer la ressource**, puis le nom du modèle de contrôle dans la liste qui s’affiche.  
  
        > [!NOTE]
        >  **Modifier un modèle** est utilisé pour appliquer des modèles de contrôle. **Modifier d’autres modèles** est utilisé pour appliquer d’autres types de modèle.  
  
     Les ressources sont applicables si elles sont compatibles. Par exemple, une ressource de pinceau peut être appliquée à la propriété **Foreground<xref:Windows.UI.Xaml.Controls.TextBox> d’un contrôle** .  
  
### <a name="to-edit-a-resource"></a>Pour modifier une ressource  
  
1.  Choisissez un élément sur la planche graphique ou dans la fenêtre Structure du document.  
  
2.  Choisissez le marqueur de propriété Par défaut ou Local à droite de la propriété dans la fenêtre Propriétés, puis choisissez **Modifier la ressource** pour ouvrir la boîte de dialogue **Modifier la ressource**.  
  
3.  Modifiez les options de la ressource.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une interface utilisateur à l’aide du concepteur XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
