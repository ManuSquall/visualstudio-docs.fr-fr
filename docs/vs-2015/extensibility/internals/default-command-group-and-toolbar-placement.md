---
title: Commande, de groupe et de positionnement de la barre d’outils par défaut | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb7144842cba237a11d94435f56782a8d2de90b6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195739"
---
# <a name="default-command-group-and-toolbar-placement"></a>Emplacement de commande, de groupe et de barre d’outils par défaut
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour l’uniformité de produit et la stabilité, l’interface utilisateur affiche certains groupes de commandes par défaut, et [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit les définitions des commandes et des groupes de commandes. Les VSPackages peuvent également utiliser les commandes standards et les groupes de commandes.  
  
 Les groupes de commandes par défaut se répartissent en trois catégories : IDE commandes, les commandes de produits et les commandes de l’éditeur.  
  
## <a name="default-ide-commands"></a>Commandes de l’IDE par défaut  
 La barre d’outils des IDE par défaut inclut des commandes partagées par tous les produits contenus dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Celles-ci comprennent les commandes relatives aux opérations de projet générique, tel que le **enregistrer** commande et le **ajouter un élément** commande. VSPackages ne devez pas ajouter ou soustraire de cette barre d’outils, à une exception près : si le produit ou un VSPackage ajoute une nouvelle fenêtre outil, la fenêtre doit être ajoutée à la liste des fenêtres Outil disponible sur le **vue** menu. Nouveaux produits ou les VSPackages peuvent ajouter leur propre barre d’outils.  
  
## <a name="default-product-commands"></a>Commandes de produit par défaut  
 Chaque produit peut fournir l’IDE avec sa propre barre d’outils par défaut qui contient un important et commandes fréquemment utilisées. Toutefois, il est préférable, à utiliser existant des menus et barres d’outils autant que possible et de les compléter avec les autres barres d’outils spécifiques aux tâches en fonction des besoins.  
  
 Le champ priorité pour une barre d’outils détermine sa position de ligne. Zéro priorité place la barre d’outils sur la troisième ligne (ligne 3), sous la barre de menus (ligne 1) et le **Standard** la barre d’outils (ligne 2). Par conséquent, les autres barres d’outils apparaissent en ligne (priorité + 3). Barres d’outils suivants sont placés sur la même ligne, si l’espace ; Sinon, ils sont automatiquement déplacés vers la ligne suivante.  
  
## <a name="default-editor-commands"></a>Commandes de l’éditeur par défaut  
 Un VSPackage qui fournit un éditeur personnalisé doit fournir une barre d’outils par défaut qui contient les plus importants et les commandes fréquemment utilisées dans cet éditeur. La barre d’outils de l’éditeur doit apparaître lorsque l’éditeur est actif et doit être masqué lorsque l’éditeur n’est pas actif. Cette visibilité est contrôlée dans le `VisibilityConstraints Element` du fichier .vsct.  
  
 Barres d’outils de l’éditeur doivent être placés au-dessous des barres d’outils IDE et produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes, les Menus et commandes définies par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

