---
title: Intégrer des modèles UML avec d’autres modèles et outils | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d1cc5a26a9c2febb0dd1dff3c0d14ba3786dde9f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764137"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Intégrer des modèles UML à d'autres modèles et outils
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les modèles UML peuvent être intégrés à d'autres modèles et à des langages spécifiques à un domaine.  
  
 Vous pouvez intégrer des modèles de différentes façons en écrivant du code d'extension pour exécuter diverses fonctions :  
  
 Attacher des références à partir de n'importe quel élément vers d'autres éléments tels que des fichiers ou vers des éléments dans d'autres modèles.  
 Dans un élément UML, vous pouvez stocker des liens vers d'autres éléments UML, vers des fichiers ou vers d'autres objets en encodant leurs identités sous forme de chaînes.  
  
 Vous pouvez par exemple écrire une extension qui peut lier une action UML (c'est-à-dire un élément dans un diagramme d'activités) à un autre diagramme d'activités. Quand l'utilisateur double-clique sur l'action, l'autre diagramme s'ouvre. Cela permet à l'utilisateur de fournir une vue plus détaillée de l'action.  
  
 Vous pouvez stocker des chaînes et d'autres données dans n'importe quel élément de deux façons :  
  
- **Propriétés de stéréotype.** Vous pouvez définir un profil UML, dans lequel vous définissez un stéréotype qui ajoute des propriétés à des types spécifiques d'éléments UML. Par exemple, vous pouvez définir un profil qui ajoute une propriété nommée **Détailssupplémentaires** à une action UML. Vous pouvez écrire du code d'extension qui stocke des données de lien dans une action en appliquant le stéréotype à l'action, puis en stockant les données dans la propriété.  
  
   Le stéréotype et ses propriétés sont visibles par l'utilisateur dans la fenêtre Propriétés.  
  
   Pour déployer cette extension, vous devez empaqueter la définition de profil et le code d'extension dans une même Extension [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
   Pour plus d’informations, consultez [définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md).  
  
   Pour un exemple de projet dans lequel un profil est déployé avec les commandes de menu et des gestionnaires de mouvements, consultez [exemple : profils UML](http://go.microsoft.com/fwlink/?LinkID=213811).  
  
- **Références.** Vous pouvez attacher un ensemble de chaînes à n'importe quel élément UML. Vous pouvez écrire du code qui stocke des informations telles qu'un nom de fichier ou le GUID d'un autre élément. Pour cela, nul besoin de fournir des définitions supplémentaires. Les références ne sont pas directement visibles par l'utilisateur.  
  
   Pour plus d’informations, consultez [attacher des chaînes de référence pour UML les éléments de modèle](../modeling/attach-reference-strings-to-uml-model-elements.md). Pour obtenir un exemple, consultez [Link UML Elements to Diagrams or autres Files](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
  Il existe deux manières d'encoder des références à des éléments de modèle :  
  
- **GUID et nom de fichier** de l’élément de modèle cible et le modèle qui le contient ou un diagramme particulier qui l’affiche.  
  
   Pour obtenir un exemple, consultez [Link UML Elements to Diagrams or autres Files](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
- **Références ModelBus.** ModelBus est une infrastructure pour la création et la résolution des références entre les modèles. Elle comprend le sélecteur ModelBus, qui permet à l'utilisateur de sélectionner un élément dans un modèle. Elle aide aussi l'utilisateur à résoudre les références qui sont perdues suite à des modifications dans le modèle cible.  
  
   Pour plus d’informations, consultez [l’intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
  Propager les modifications d'un modèle à un autre.  
  Par exemple, vous pouvez synchroniser le nom d'un élément avec le nom du diagramme lié pour que si l'utilisateur modifie l'un, l'autre change également. Pour cela, il existe deux mécanismes :  
  
1. **Les règles VMSDK** peut être utilisé pour propager les modifications à l’intérieur du même modèle.  
  
    Pour obtenir un exemple, consultez [Link UML Elements to Diagrams or autres Files](http://go.microsoft.com/fwlink/?LinkId=213813).  
  
2. **Événements VMSDK** peut être utilisé pour propager les modifications en dehors du modèle – par exemple, pour modifier le nom de fichier d’un document lié ou pour modifier un élément dans un autre modèle.  
  
   Pour plus d’informations sur ces deux mécanismes, consultez [Comment : répondre aux modifications dans un modèle UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).  
  
   Faire glisser les éléments pour les copier d'un modèle à un autre  
   Vous pouvez laisser l'utilisateur créer des éléments en les faisant glisser sur un diagramme UML. Il n'est pas obligatoire que l'élément créé soit une copie de l'original. Vous pouvez par exemple laisser l'utilisateur faire glisser un diagramme d'activités de l'Explorateur de solutions vers un autre diagramme d'activités pour créer une nouvelle action.  
  
   Pour plus d’informations, consultez [définir un gestionnaire de mouvements sur un diagramme de modélisation](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) et [Comment : ajouter un gestionnaire glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="samples"></a>Exemples  
 Consultez l’exemple de code [Link UML Elements to Diagrams or autres Files](http://go.microsoft.com/fwlink/?LinkId=213813). Cet exemple permet aux utilisateurs de faire glisser un fichier sur n'importe quel élément UML et d'ouvrir ultérieurement le fichier en double-cliquant sur l'élément. Vous pouvez par exemple lier un diagramme d'activités à un élément de cas d'usage. Une icône indique les éléments qui ont des liens.  
  
 Cet exemple de code illustre les techniques suivantes :  
  
- [Attacher des chaînes de référence à des éléments de modèle UML](../modeling/attach-reference-strings-to-uml-model-elements.md)  
  
   L'exemple de code stocke des chemins de fichiers et des GUID d'éléments dans des chaînes de référence qui sont associées à l'élément.  
  
- Comment ajouter des éléments décoratifs à des éléments UML. Pour obtenir des informations générales sur les éléments décoratifs, consultez [personnalisation des champs de texte et Image](../modeling/customizing-text-and-image-fields.md).  
  
   L'exemple ajoute un élément décoratif d'image aux formes UML.  
  
- [Guide pratique pour répondre à des modifications dans un modèle UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)  
  
   L'exemple montre comment définir une règle qui répond à l'apparition de nouvelles formes sur un diagramme.  
  
- [Définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [Définir un gestionnaire de mouvements sur un diagramme de modélisation](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)  
  
   L'exemple montre comment gérer les éléments déplacés à partir de l'Explorateur Windows (ou de l'Explorateur de fichiers), de l'Explorateur de solutions et d'autres éléments UML.  
  
  Pour un exemple dans lequel un modèle UML est lue par un DSL, consultez [Comment : ajouter un gestionnaire glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Définir un gestionnaire de mouvements sur un diagramme de modélisation](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)   
 [Comment : ajouter un gestionnaire glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Comment : répondre aux modifications dans un modèle UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)   
 [Exemple : Les profils UML](http://go.microsoft.com/fwlink/?LinkID=213811)   
 [Link UML Elements to Diagrams or other Files](http://go.microsoft.com/fwlink/?LinkId=213813)



