---
title: Référence (Capture par programmation) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70581d468c32964d7e081ec0ee4af3fe411b71b9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504392"
---
# <a name="reference-programmatic-capture"></a>Référence (capture par programmation)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [référence (Capture par programmation)](https://docs.microsoft.com/visualstudio/debugger/graphics/reference-programmatic-capture).  
  
Graphics Diagnostics prend en charge le contrôle par programme de ses fonctionnalités de capture par l’intermédiaire de l’API de capture par programme. Vous pouvez utiliser cette API pour activer/désactiver et ajouter des messages au HUD (Head-Up Display) de diagnostics graphiques, initialiser et créer des fichiers journaux graphiques, et capturer des informations graphiques.  
  
## <a name="programmatic-capture-apis"></a>API de capture par programme  
  
### <a name="classes"></a>Classes  
  
|Nom|Description|  
|----------|-----------------|  
|[VsgDbg Class](../debugger/vsgdbg-class.md)|Représente l’interface par l’intermédiaire de laquelle le composant dans l’application Graphics Diagnostics est contrôlé par programme.|  
  
### <a name="preprocessor-symbols"></a>Symboles du préprocesseur  
  
|Name|Description|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)|Définit par sa présence si le fichier journal graphique est enregistré dans le répertoire des fichiers temporaires de l'utilisateur.|  
|[VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)|Définit le nom de fichier par défaut du fichier journal graphique.|  
|[VSG_NODEFAULT_INSTANCE](../debugger/vsg-nodefault-instance.md)|Définit par sa présence si une instance par défaut de la classe `VsgDbg` est fournie.|  
  
## <a name="related-articles"></a>Articles connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Capture d’informations graphiques](../debugger/capturing-graphics-information.md)|Vous pouvez capturer les informations graphiques de votre application basée sur DirectX de manière à utiliser les outils Graphics Diagnostics [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour diagnostiquer les problèmes de rendu.|  
|[Vue d’ensemble](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Montre comment Graphics Diagnostics peut vous aider à déboguer les erreurs de rendu dans les applications et jeux DirectX.|



