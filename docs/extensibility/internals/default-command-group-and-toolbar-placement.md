---
title: Placement par défaut de commande, de groupe et de barre d’outils (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b432b514231e876dda1393bad8a315030272d998
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708893"
---
# <a name="default-command-group-and-toolbar-placement"></a>Placement par défaut de commande, de groupe et de barre d’outils
Pour l’uniformité et la stabilité des produits, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur affiche certains groupes de commandement par défaut et fournit des définitions pour les commandes et les groupes de commandement. VSPackages peut également utiliser les commandes standard et les groupes de commandement.

 Les groupes de commandement par défaut se divisent en trois catégories : commandes IDE, commandes de produits et commandes d’éditeurs.

## <a name="default-ide-commands"></a>Commandes IDE par défaut
 La barre d’outils IDE par défaut [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]comprend des commandes partagées par tous les produits contenus dans . Il s’agit notamment de commandes relatives aux opérations génériques du projet, telles que la commande **Save** et la commande **Add Item.** VSPackages ne doit pas ajouter ou soustraire à cette barre d’outils, à une exception près: Si le produit ou VSPackage ajoute une nouvelle fenêtre d’outil, alors la fenêtre doit être ajoutée à la liste des fenêtres d’outils disponibles sur le menu **View.** De nouveaux produits ou VSPackages peuvent ajouter leur propre barre d’outils.

## <a name="default-product-commands"></a>Commandes de produits par défaut
 Chaque produit peut fournir à l’IDE sa propre barre d’outils par défaut qui contient des commandes importantes et fréquemment utilisées. Il est préférable, cependant, d’utiliser les menus existants et les barres d’outils chaque fois que possible et de les compléter avec d’autres barres d’outils spécifiques aux tâches au besoin.

 Le champ prioritaire pour une barre d’outils détermine son placement en ligne. Zéro priorité place la barre d’outils sur la troisième rangée (rangée 3), sous la barre de menu (rangée 1) et la barre d’outils **Standard** (ligne 2). Par conséquent, d’autres barres d’outils apparaissent en ligne (priorité 3). Les barres d’outils suivantes sont placées sur la même rangée, s’il y a de la place; sinon, ils sont automatiquement déplacés à la rangée suivante.

## <a name="default-editor-commands"></a>Commandes d’éditeur par défaut
 Un VSPackage qui fournit un éditeur personnalisé devrait fournir une barre d’outils par défaut qui contient les commandes les plus importantes et fréquemment utilisées dans cet éditeur. La barre d’outils de l’éditeur doit apparaître lorsque l’éditeur est actif et doit être masqué lorsque l’éditeur n’est pas actif. Cette visibilité est contrôlée `VisibilityConstraints` dans l’élément du fichier *.vsct.*

 Les barres d’outils de l’éditeur doivent être placées en dessous des barres d’outils IDE et des barres d’outils de produits.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et groupes définis par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
