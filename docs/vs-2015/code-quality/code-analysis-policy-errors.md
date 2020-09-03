---
title: Erreurs de stratégie d’analyse du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8cb50fffc1411e77f771b0f74fbb947144eb6017
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672924"
---
# <a name="code-analysis-policy-errors"></a>Code Analysis Policy Errors
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les erreurs suivantes se produisent si la stratégie d’analyse du code n’est pas satisfaite lors de l’archivage :

 **Les paramètres d’analyse du code pour un ou plusieurs projets ne sont pas compatibles avec la stratégie d’analyse du code.**

 La configuration requise pour l’analyse du code dans le contrôle de code source du projet d’équipe n’a pas été satisfaite pour un ou plusieurs projets de code. Cette erreur peut être causée par une ou plusieurs des conditions suivantes :

1. L’analyse du code n’est pas activée sur la build pour tous les projets de la solution.

2. L’ensemble de règles local pour le projet dans Visual Studio a un paramètre d' **action** moins restrictif que celui défini par l’utilisateur dans la règle de projet d’équipe. par exemple, une règle définie sur erreur d' **action** = **Error** sur le serveur a son **action** définie sur **Avertissement** ou **aucun** dans l’ensemble de règles en cours d’exécution dans Visual Studio.

3. L’ensemble de règles spécifié dans Visual Studio ne contient pas toutes les règles qui sont spécifiées dans l’ensemble de règles spécifié dans la stratégie d’archivage de l’analyse du code pour le projet d’équipe.

   **Échec de la stratégie d’analyse du code. Des erreurs se sont produites dans Project {0} ou la build n’est pas à jour.**

   Soit la Build contient des erreurs, soit les erreurs ont été corrigées, mais l’analyse du code n’a pas été effectuée après le correctif.

   **Échec de l’archivage. La stratégie d’analyse du code requiert l’archivage par le biais de Visual Studio avec une solution ouverte.**

   La stratégie d’analyse du code requiert que tous les fichiers archivés soient dans la solution actuellement ouverte. Pour corriger cette erreur, ouvrez la solution qui contient le fichier à archiver.

   **Tous les fichiers de l’archivage en attente ne se trouvent pas dans la solution actuellement ouverte.**

   La stratégie d’analyse du code requiert que tous les fichiers archivés soient dans la solution actuellement ouverte. Cette erreur se produit lorsqu’il existe une solution ouverte, mais que certains fichiers de la vue « archivage en attente » ne font pas partie de la solution actuellement ouverte. Pour corriger cette erreur, ouvrez la solution qui contient le fichier à archiver.

   **La version de « {0} » n’est pas correcte. Le nom fort spécifié dans la stratégie est « {1} ».**

   Cette erreur s’applique aux projets .NET. Une règle. dll requise par la stratégie d’analyse du code existe sur l’ordinateur local, mais la version/la clé publique ne correspond pas. Pour corriger cette erreur, le créateur de la stratégie doit mettre à jour le fichier. dll dans le répertoire *C:\Program Files\Microsoft Visual \\ Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules* sur son ordinateur.

   **{0}l’assembly' 'spécifié dans la stratégie n’existe pas.**

   Cette erreur s’applique aux projets .NET. La dll correspondante n’est pas installée sur l’ordinateur client pour une règle requise par la stratégie d’analyse du code. Pour corriger cette erreur, le créateur de la stratégie doit mettre à jour la dll dans le répertoire *C:\Program Files\Microsoft Visual Studio \\ 8 \ Team Tools\Static Analysis Tools\FxCop\Rules* sur son ordinateur.

   **{0}Les paramètres de règle de projet ne sont pas conformes à la stratégie d’analyse du code.**

   Cette erreur s’applique aux projets .NET. Les paramètres de règles de code managé ne sont pas aussi stricts que la stratégie l’exige. Pour corriger cette erreur, le paramètre client doit être identique ou plus strict que l’exigence de stratégie sur le serveur.

   **L’analyse du code n’est pas activée sur la configuration active. Basculez vers le projet de configuration {0} et de génération {1} avant d’archiver.**

   Dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , l’analyse du code n’est pas activée pour la configuration active, mais au moins une analyse du code est activée.

   **Vous devez activer l’analyse du code pour les fichiers binaires managés dans {0} les propriétés du projet et la génération avant d’archiver.**

   Cette erreur s’applique aux [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] applications .net. La stratégie requiert l’exécution de l’analyse du code managé, mais elle n’est pas activée dans le projet actuel sur le client.

   **Vous devez activer l’analyse du code dans {0} les propriétés et la génération du projet avant d’archiver.**

   Cette erreur est appliquée aux [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projets et aux projets Web. La stratégie requiert l’exécution de l’analyse du code managé, mais elle n’est pas activée dans le projet actuel sur le client.

   **Vous devez activer l’analyse du code C/C++ dans {0} les propriétés du projet et la génération avant d’archiver.**

   Cette erreur s’applique aux projets non managés. La stratégie d’analyse du code requiert l’analyse du code pour C/C++, mais elle n’est pas activée dans le projet actuel sur le client.

## <a name="see-also"></a>Voir aussi
 [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md)
