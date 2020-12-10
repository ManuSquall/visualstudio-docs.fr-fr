---
title: Référence (capture par programmation) | Microsoft Docs
description: Utilisez l’API de capture par programmation pour exercer un contrôle par programmation sur les fonctionnalités de capture de Graphics Diagnostics.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 30cf44d6d16da46e9d6f08ffae4971d35136db58
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996108"
---
# <a name="reference-programmatic-capture"></a>Référence (capture par programmation)
Graphics Diagnostics prend en charge le contrôle par programme de ses fonctionnalités de capture par l’intermédiaire de l’API de capture par programme. Vous pouvez utiliser cette API pour activer/désactiver et ajouter des messages au HUD (Head-Up Display) de diagnostics graphiques, initialiser et créer des fichiers journaux graphiques, et capturer des informations graphiques.

## <a name="programmatic-capture-apis"></a>API de capture par programme

### <a name="classes"></a>Classes

|Nom|Description|
|----------|-----------------|
|[VsgDbg, classe](vsgdbg-class.md)|Représente l'interface par l'intermédiaire de laquelle le composant dans l'application des diagnostics graphiques est contrôlé par programme.|

### <a name="preprocessor-symbols"></a>Symboles du préprocesseur

|Nom|Description|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Définit par sa présence si le fichier journal graphique est enregistré dans le répertoire des fichiers temporaires de l'utilisateur.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Définit le nom de fichier par défaut du fichier journal graphique.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Définit par sa présence si une instance par défaut de la classe `VsgDbg` est fournie.|

## <a name="related-articles"></a>Articles connexes

| Titre | Description |
| - | - |
| [Capture d'informations graphiques](capturing-graphics-information.md) | Vous pouvez capturer les informations graphiques de votre application basée sur DirectX de manière à utiliser les outils Graphics Diagnostics [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour diagnostiquer les problèmes de rendu. |
| [Vue d'ensemble](overview-of-visual-studio-graphics-diagnostics.md) | Montre comment Graphics Diagnostics peut vous aider à déboguer les erreurs de rendu dans les applications et jeux DirectX. |
