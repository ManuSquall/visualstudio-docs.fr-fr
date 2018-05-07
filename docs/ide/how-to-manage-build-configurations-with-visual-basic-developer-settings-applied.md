---
title: Guide pratique pour gérer des configurations de build en appliquant les paramètres du développeur Visual Basic
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, building with Visual Basic settings
- MSBuild, debug build
- advanced build configurations
- building with Visual Basic developer settings
- debug builds
- MSBuild, release build
- release builds
ms.assetid: eaea6e0b-6c61-4869-8d63-d372c745a23c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 987419e62d54b44a21a70f625e2a240bd7aecc21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-manage-build-configurations-with-visual-basic-developer-settings-applied"></a>Guide pratique pour gérer des configurations de build en appliquant les paramètres du développeur Visual Basic

Par défaut, toutes les options de configuration de build avancées sont masquées lorsque les paramètres de développeur Visual Basic sont appliqués. Cette rubrique explique comment activer manuellement ces paramètres.

## <a name="enable-advanced-build-configurations"></a>Activer les configurations de build avancées

Par défaut, les paramètres de développeur Visual Basic masquent l’option permettant d’ouvrir la boîte de dialogue **Gestionnaire de configuration** et les listes **Configuration** et **Plateforme** dans le [ Concepteur de projets](..//ide/reference/application-page-project-designer-visual-basic.md).

1.  Dans le menu **Outils** , cliquez sur **Options**.

2.  Développez **Projets et solutions** et cliquez sur **Général**.

    > [!NOTE]
    > Le nœud **Général** est visible même si l’option **Afficher tous les paramètres** est désactivée. Si vous souhaitez afficher toutes les options disponibles, cliquez sur **Afficher tous les paramètres**.

3.  Cliquez sur **Afficher les configurations de build avancées**.

4.  Cliquez sur **OK**.

     Dans le menu **Build**, le **Gestionnaire de configurations** est désormais disponible. De plus, les listes **Configuration** et **Plateforme** sont visibles dans le **Concepteur de projet**.

## <a name="see-also"></a>Voir aussi

- [Présentation des configurations de build](../ide/understanding-build-configurations.md)
- [Compiler et générer](../ide/compiling-and-building-in-visual-studio.md)