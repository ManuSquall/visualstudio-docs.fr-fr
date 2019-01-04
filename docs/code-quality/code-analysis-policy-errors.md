---
title: Erreurs de stratégie d’analyse du code
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.codeanalysis.policyfailures
helpviewer_keywords:
- policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3edd9b341d2ccead65fee8f97f32ec54f7857dea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987808"
---
# <a name="code-analysis-policy-errors"></a>Erreurs de stratégie d’analyse du code

Les erreurs suivantes se produisent si la stratégie d’analyse de code n’est pas satisfaite à l’archivage :

**Les paramètres d’analyse du Code pour un ou plusieurs projets ne sont pas compatibles avec la stratégie d’analyse du Code.**

Les exigences d’analyse de code la vérification le contrôle de code source du projet n’a pas été remplie pour un ou plusieurs projets de code. Cette erreur peut être causée par une ou plusieurs des conditions suivantes :

- Analyse du code n’est pas activée sur la build pour tous les projets dans la solution.

- Règle locale définie pour le projet dans Visual Studio comporte moins restrictif **Action** définissant à la règle de projet définie par exemple, une règle est définie sur **Action**=**erreur** sur le serveur a sa **Action** définie sur **avertissement** ou **aucun** dans l’ensemble en cours d’exécution dans Visual Studio de règles).

- L’ensemble spécifié dans Visual Studio de règles ne contient pas toutes les règles qui sont spécifiés dans l’ensemble spécifié dans la stratégie de vérification de l’analyse du Code pour le projet de règles.

**Échec de la stratégie d’analyse du Code. Il existe des erreurs dans le projet {0} ou la build n’est pas à jour.**

La génération contient des erreurs ou les erreurs ont été résolus, mais l’analyse du code n’a pas été effectuée après la correction.

**Échec de l’archivage. La stratégie d’analyse de Code requiert que vous archivez via Visual Studio avec une solution ouverte.**

La stratégie d’analyse de code requiert que tous les fichiers en cours d’archivage doivent être dans la solution actuellement ouverte. Pour corriger cette erreur, ouvrez la solution qui contient le fichier à archiver.

**Pas de tous les fichiers dans l’archivage en attente se trouvent dans la solution actuellement ouverte.**

La stratégie d’analyse de code requiert que tous les fichiers en cours d’archivage doivent être dans la solution actuellement ouverte. Cette erreur est générée lorsqu’il existe une solution ouverte, mais certains fichiers dans la vue « archivage en attente » ne font pas partie de la solution actuellement ouverte. Pour corriger cette erreur, ouvrez la solution qui contient le fichier à archiver.

**La version de '{0}' n’est pas correct. Le nom fort spécifié dans la stratégie est «{1}».**

Cette erreur s’applique aux projets .NET. Un fichier .dll de règle requise par la stratégie d’analyse de code existe sur l’ordinateur local, mais la version/clé publique ne correspond pas. Pour corriger cette erreur, le créateur de la stratégie doit mettre à jour les fichiers .dll dans *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  répertoire sur leur ordinateur.

**'{0}' assembly spécifié dans la stratégie n’existe pas.**

Cette erreur s’applique aux projets .NET. Une règle requise par la stratégie d’analyse de code n’a pas la dll correspondante installée sur l’ordinateur client. Pour corriger cette erreur, le créateur de la stratégie doit mettre à jour la dll dans *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  répertoire sur leur ordinateur.

**Projet {0} paramètres de règle ne sont pas en conformité avec la stratégie d’analyse du Code.**

Cette erreur s’applique aux projets .NET. Les paramètres de règles de code managé ne sont pas aussi strictes que nécessite la stratégie. Pour corriger cette erreur, le paramètre client doit être identiques ou plus strict que l’exigence de stratégie sur le serveur.

**Analyse du code n’est pas activée pour la configuration active. Basculer vers la configuration {0} et générez le projet {1} avant d’archiver.**

Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la configuration active n’a pas activé l’analyse du code, mais il existe au moins une analyse du code activée.

**Vous devez activer l’analyse du Code pour les fichiers binaires managés dans le projet {0} build avant d’archiver et propriétés.**

Cette erreur s’applique aux [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] applications .NET. La stratégie nécessite l’analyse du code managé à exécuter, mais il n’est pas activé dans le projet actuel sur le client.

**Vous devez activer l’analyse du Code de projet {0} build avant d’archiver et propriétés.**

Cette erreur s’appliquée aux [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projets et des projets web. La stratégie nécessite l’analyse du code managé à exécuter, mais il n’est pas activé dans le projet actuel sur le client.

**Vous devez activer l’analyse du Code C/C++ dans le projet {0} build avant d’archiver et propriétés.**

Cette erreur s’applique aux projets non managés. La stratégie d’analyse de code nécessite l’analyse du Code pour C/C++, mais il n’est pas activé dans le projet actuel sur le client.

## <a name="see-also"></a>Voir aussi

- [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md)