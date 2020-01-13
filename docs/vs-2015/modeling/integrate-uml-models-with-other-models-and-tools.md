---
title: Intégrer des modèles UML à d’autres modèles et outils | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ea0c562bb9c2a8050fc1365fac19df20232f80
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918351"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Intégrer des modèles UML à d'autres modèles et outils
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les modèles UML peuvent être intégrés à d'autres modèles et à des langages spécifiques à un domaine.

 Vous pouvez intégrer des modèles de différentes façons en écrivant du code d'extension pour exécuter diverses fonctions :

 Attacher des références à partir de n'importe quel élément vers d'autres éléments tels que des fichiers ou vers des éléments dans d'autres modèles.
Dans un élément UML, vous pouvez stocker des liens vers d'autres éléments UML, vers des fichiers ou vers d'autres objets en encodant leurs identités sous forme de chaînes.

 Vous pouvez par exemple écrire une extension qui peut lier une action UML (c'est-à-dire un élément dans un diagramme d'activités) à un autre diagramme d'activités. Quand l'utilisateur double-clique sur l'action, l'autre diagramme s'ouvre. Cela permet à l'utilisateur de fournir une vue plus détaillée de l'action.

 Vous pouvez stocker des chaînes et d'autres données dans n'importe quel élément de deux façons :

- **Propriétés du stéréotype.** Vous pouvez définir un profil UML, dans lequel vous définissez un stéréotype qui ajoute des propriétés à des types spécifiques d'éléments UML. Par exemple, vous pouvez définir un profil qui ajoute une propriété nommée **détailssupplémentaires** à une action UML. Vous pouvez écrire du code d'extension qui stocke des données de lien dans une action en appliquant le stéréotype à l'action, puis en stockant les données dans la propriété.

   Le stéréotype et ses propriétés sont visibles par l'utilisateur dans la fenêtre Propriétés.

   Pour déployer cette extension, vous devez empaqueter la définition de profil et le code d'extension dans une même Extension [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   Pour plus d’informations, consultez [définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md).

- **Référence.** Vous pouvez attacher un ensemble de chaînes à n'importe quel élément UML. Vous pouvez écrire du code qui stocke des informations telles qu'un nom de fichier ou le GUID d'un autre élément. Pour cela, nul besoin de fournir des définitions supplémentaires. Les références ne sont pas directement visibles par l'utilisateur.

Il existe deux manières d'encoder des références à des éléments de modèle :

- **GUID et nom de fichier** de l’élément de modèle cible et du modèle qui le contient, ou un diagramme particulier qui l’affiche.

- **Références ModelBus.** ModelBus est une infrastructure pour la création et la résolution des références entre les modèles. Elle comprend le sélecteur ModelBus, qui permet à l'utilisateur de sélectionner un élément dans un modèle. Elle aide aussi l'utilisateur à résoudre les références qui sont perdues suite à des modifications dans le modèle cible.

   Pour plus d’informations, consultez [intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

  Propager les modifications d'un modèle à un autre.
  Par exemple, vous pouvez synchroniser le nom d'un élément avec le nom du diagramme lié pour que si l'utilisateur modifie l'un, l'autre change également. Pour cela, il existe deux mécanismes :

1. Les **règles VMSDK** peuvent être utilisées pour propager les modifications à l’intérieur du même modèle.

2. Les **événements VMSDK** peuvent être utilisés pour propager des modifications en dehors du modèle, par exemple pour modifier le nom de fichier d’un document lié, ou pour modifier un élément dans un autre modèle.

   Pour plus d’informations sur ces deux mécanismes, consultez [Comment : répondre à des modifications dans un modèle UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

   Faites glisser des éléments pour les copier d’un modèle à un autre. vous pouvez laisser l’utilisateur créer des éléments en faisant glisser des éléments sur un diagramme UML. Il n'est pas obligatoire que l'élément créé soit une copie de l'original. Vous pouvez par exemple laisser l'utilisateur faire glisser un diagramme d'activités de l'Explorateur de solutions vers un autre diagramme d'activités pour créer une nouvelle action.

   Pour plus d’informations, consultez [définir un gestionnaire de mouvements sur un diagramme de modélisation](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) et [Comment : ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="see-also"></a>Voir aussi
 [Définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [définir un gestionnaire de mouvements sur un diagramme de modélisation](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [Comment : ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md) [Comment : répondre aux modifications dans un modèle UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)
