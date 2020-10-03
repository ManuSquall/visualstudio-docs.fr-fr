---
title: Prise en charge de DirectX 12 dans Visual Studio | Microsoft Docs
description: Les utilisateurs de DirectX 12 sont recommandés pour utiliser PIX sur Windows pour une expérience de débogage graphique complète
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 9dbc52a0233abe467da4d41af0134663bc7cd9df
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671396"
---
# <a name="directx-12-support-in-visual-studio"></a>Prise en charge de DirectX 12 dans Visual Studio

## <a name="directx-12-support"></a>Prise en charge DirectX 12

Visual Studio Graphics Diagnostics ne prend pas en charge les jeux DirectX 12. Pour le débogage graphique avec la prise en charge complète de DirectX 12, Visual Studio recommande *pix sur Windows*. 

PIX sur Windows est un outil de réglage et de débogage des performances avec des fonctionnalités à distance. PIX sur Windows offre sept fonctionnalités principales qui répondent à vos besoins de débogage graphiques. Déboguez et analysez les performances du rendu graphique Direct3D 12 avec les captures GPU. Comprenez les performances et les threads de toutes les tâches processeur et GPU effectuées par votre jeu avec des captures temporelles. Identifiez les inefficacités dans les modèles d’e/s disque de votre titre et la disposition des packages avec des captures d’e/s de fichier.

Appuyez-vous sur votre parcours de débogage graphique avec [**pix sur Windows**](https://aka.ms/PIXonWindows).

[**Téléchargez pix sur Windows**](https://aka.ms/downloadPIX) ou [ **consultez la documentation**.](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>PIX sur Windows

PIX sur Windows propose sept principaux modes de fonctionnement :
1. **Captures GPU** pour le débogage et l’analyse des performances du rendu graphique Direct3D 12.
2. **Captures temporelles** pour comprendre les performances et les threads de toutes les tâches processeur et GPU effectuées par votre jeu, et pour le suivi de l’utilisation de la mémoire GPU.
3. Les **captures de résumé des fonctions** accumulent des informations sur la durée d’exécution de chaque fonction et sur la fréquence à laquelle chaque fonction est appelée.
4. Les **captures graphique des appels** tracent l’exécution d’une fonction unique.
5. Les **captures d’allocation de mémoire** offrent un aperçu des allocations de mémoire effectuées par votre jeu.
6. Les **captures d’e/s de fichier** vous aident à identifier les inefficacités dans les modèles d’e/s disque de votre titre et la disposition des packages.
7. Le **Moniteur système** affiche des données de compteur en temps réel pendant l’exécution d’un jeu.

Une présentation vidéo détaillée de PIX sur Windows est disponible [ **ici**](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB)
