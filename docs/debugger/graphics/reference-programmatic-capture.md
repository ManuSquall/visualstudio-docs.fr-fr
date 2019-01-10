---
title: Référence (Capture par programmation) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 826b399aa0ad0b5a45bc6fd80eb73b555cb3f01c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836345"
---
# <a name="reference-programmatic-capture"></a>Référence (capture par programmation)
Graphics Diagnostics prend en charge le contrôle par programme de ses fonctionnalités de capture par l’intermédiaire de l’API de capture par programme. Vous pouvez utiliser cette API pour activer/désactiver et ajouter des messages au HUD (Head-Up Display) de diagnostics graphiques, initialiser et créer des fichiers journaux graphiques, et capturer des informations graphiques.  

## <a name="programmatic-capture-apis"></a>API de capture par programme  

### <a name="classes"></a>Classes  

|Name|Description|  
|----------|-----------------|  
|[VsgDbg Class](vsgdbg-class.md)|Représente l’interface par l’intermédiaire de laquelle le composant dans l’application Graphics Diagnostics est contrôlé par programme.|  

### <a name="preprocessor-symbols"></a>Symboles du préprocesseur  

|Name|Description|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Définit par sa présence si le fichier journal graphique est enregistré dans le répertoire des fichiers temporaires de l'utilisateur.|  
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Définit le nom de fichier par défaut du fichier journal graphique.|  
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Définit par sa présence si une instance par défaut de la classe `VsgDbg` est fournie.|  

## <a name="related-articles"></a>Articles connexes  

| Titre | Description |
| - | - |
| [Capturing Graphics Information](capturing-graphics-information.md) | Vous pouvez capturer les informations graphiques de votre application basée sur DirectX de manière à utiliser les outils Graphics Diagnostics [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pour diagnostiquer les problèmes de rendu. |
| [Vue d’ensemble](overview-of-visual-studio-graphics-diagnostics.md) | Montre comment Graphics Diagnostics peut vous aider à déboguer les erreurs de rendu dans les applications et jeux DirectX. |
