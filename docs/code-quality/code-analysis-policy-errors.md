---
title: Erreurs de stratégie d’analyse du code
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e6ff6000f0eab60e17642bf2bd8257154e54a9d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745955"
---
# <a name="code-analysis-policy-errors"></a>Erreurs de stratégie d’analyse du code

Les erreurs suivantes se produisent si la stratégie d’analyse du code n’est pas satisfaite lors de l’archivage :

**Les paramètres d’analyse du code pour un ou plusieurs projets ne sont pas compatibles avec la stratégie d’analyse du code.**

La configuration requise pour l’analyse du code dans le contrôle de code source du projet n’a pas été satisfaite pour un ou plusieurs projets de code. Cette erreur peut être causée par une ou plusieurs des conditions suivantes :

- L’analyse du code n’est pas activée sur la build pour tous les projets de la solution.

- L’ensemble de règles local pour le projet dans Visual Studio a un paramètre d' **action** moins restrictif que la règle de projet définie par exemple, une règle qui est définie sur **action**=**erreur** sur le serveur a son **action** définie sur **Avertissement** ou **Aucune** dans l’ensemble de règles en cours d’exécution dans Visual Studio).

- L’ensemble de règles spécifié dans Visual Studio ne contient pas toutes les règles qui sont spécifiées dans l’ensemble de règles spécifié dans la stratégie d’archivage de l’analyse du code pour le projet.

**Échec de la stratégie d’analyse du code. Le projet {0} contient des erreurs ou la build n’est pas à jour.**

Soit la Build contient des erreurs, soit les erreurs ont été corrigées, mais l’analyse du code n’a pas été effectuée après le correctif.

**Échec de l’archivage. La stratégie d’analyse du code requiert l’archivage par le biais de Visual Studio avec une solution ouverte.**

La stratégie d’analyse du code requiert que tous les fichiers archivés soient dans la solution actuellement ouverte. Pour corriger cette erreur, ouvrez la solution qui contient le fichier à archiver.

**Tous les fichiers de l’archivage en attente ne se trouvent pas dans la solution actuellement ouverte.**

La stratégie d’analyse du code requiert que tous les fichiers archivés soient dans la solution actuellement ouverte. Cette erreur se produit lorsqu’il existe une solution ouverte, mais que certains fichiers de la vue « archivage en attente » ne font pas partie de la solution actuellement ouverte. Pour corriger cette erreur, ouvrez la solution qui contient le fichier à archiver.

**La version de' {0} 'n’est pas correcte. Le nom fort spécifié dans la stratégie est « {1} ».**

Cette erreur s’applique aux projets .NET. Une règle. dll requise par la stratégie d’analyse du code existe sur l’ordinateur local, mais la version/la clé publique ne correspond pas. Pour corriger cette erreur, le créateur de la stratégie doit mettre à jour le fichier. dll dans *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* Directory sur son ordinateur.

**l’assembly' {0} 'spécifié dans la stratégie n’existe pas.**

Cette erreur s’applique aux projets .NET. La dll correspondante n’est pas installée sur l’ordinateur client pour une règle requise par la stratégie d’analyse du code. Pour corriger cette erreur, le créateur de la stratégie doit mettre à jour la dll dans *C:\Program Files\Microsoft Visual Studio 8 \ Team Tools\Static Analysis Tools\FxCop\Rules \\* Directory sur son ordinateur.

**Les paramètres de règle {0} de Project ne sont pas conformes à la stratégie d’analyse du code.**

Cette erreur s’applique aux projets .NET. Les paramètres de règles de code managé ne sont pas aussi stricts que la stratégie l’exige. Pour corriger cette erreur, le paramètre client doit être identique ou plus strict que l’exigence de stratégie sur le serveur.

**L’analyse du code n’est pas activée sur la configuration active. Basculez vers la configuration {0} et générez le projet {1} avant d’archiver.**

Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], l’analyse du code n’est pas activée pour la configuration active, mais au moins une analyse du code est activée.

**Vous devez activer l’analyse du code pour les fichiers binaires managés dans les propriétés Project {0} et les générer avant d’archiver.**

Cette erreur s’applique aux applications [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] .NET. La stratégie requiert l’exécution de l’analyse du code managé, mais elle n’est pas activée dans le projet actuel sur le client.

**Vous devez activer l’analyse du code dans les propriétés de Project {0} et générer avant d’archiver.**

Cette erreur s’est appliquée aux projets [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et aux projets Web. La stratégie requiert l’exécution de l’analyse du code managé, mais elle n’est pas activée dans le projet actuel sur le client.

**Vous devez activer l’analyseC++ C/code dans les propriétés et la génération du projet {0} avant d’archiver.**

Cette erreur s’applique aux projets non managés. La stratégie d’analyse du code requiert l’analyse duC++code pour C/, mais elle n’est pas activée dans le projet actuel sur le client.

## <a name="see-also"></a>Voir aussi

- [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md)
