---
title: Positionnement de la commande, du groupe et de la barre d’outils par défaut | Microsoft Docs
description: Découvrez les commandes de l’IDE, les commandes du produit et les commandes de l’éditeur, que l’interface utilisateur de Visual Studio affiche par défaut.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1c38abc09b0d5c8996cde44d33f4778a54a0cd62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902955"
---
# <a name="default-command-group-and-toolbar-placement"></a>Positionnement par défaut des commandes, des groupes et des barres d’outils
Pour l’uniformité et la stabilité des produits, l’interface utilisateur affiche certains groupes de commandes par défaut et [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit des définitions pour les commandes et les groupes de commandes. Les VSPackages peuvent également utiliser les commandes et les groupes de commandes standard.

 Les groupes de commandes par défaut se répartissent en trois catégories : les commandes IDE, les commandes du produit et les commandes de l’éditeur.

## <a name="default-ide-commands"></a>Commandes IDE par défaut
 La barre d’outils IDE par défaut comprend des commandes partagées par tous les produits contenus dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Celles-ci incluent des commandes relatives aux opérations de projet génériques, telles que la commande **Enregistrer** et la commande **Ajouter un élément** . Les VSPackages ne doivent pas ajouter ni soustraire cette barre d’outils, à une exception près : si le produit ou le VSPackage ajoute une nouvelle fenêtre outil, la fenêtre doit être ajoutée à la liste des fenêtres d’outils disponibles dans le menu **affichage** . Les nouveaux produits ou VSPackages peuvent ajouter leur propre barre d’outils.

## <a name="default-product-commands"></a>Commandes de produit par défaut
 Chaque produit peut fournir à l’IDE sa propre barre d’outils par défaut qui contient des commandes importantes et fréquemment utilisées. Toutefois, il est préférable d’utiliser des menus et des barres d’outils existants chaque fois que cela est possible et de les compléter avec d’autres barres d’outils spécifiques aux tâches si nécessaire.

 Le champ priorité d’une barre d’outils détermine son emplacement de ligne. La priorité zéro place la barre d’outils sur la troisième ligne (ligne 3), sous la barre de menus (ligne 1) et la barre d’outils **standard** (ligne 2). Par conséquent, les autres barres d’outils apparaissent à la ligne (priorité + 3). Les barres d’outils suivantes sont placées sur la même ligne, s’il y a de la place ; dans le cas contraire, ils sont automatiquement déplacés vers la ligne suivante.

## <a name="default-editor-commands"></a>Commandes de l’éditeur par défaut
 Un VSPackage qui fournit un éditeur personnalisé doit fournir une barre d’outils par défaut qui contient les commandes les plus importantes et les plus fréquemment utilisées dans cet éditeur. La barre d’outils de l’éditeur doit s’afficher lorsque l’éditeur est actif et doit être masqué lorsque l’éditeur n’est pas actif. Cette visibilité est contrôlée dans l' `VisibilityConstraints` élément du fichier *. vsct* .

 Les barres d’outils de l’éditeur doivent être placées sous l’IDE et les barres d’outils du produit.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et groupes définis par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)
- [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
