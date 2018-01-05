---
title: "Erreurs de stratégie d’analyse de code | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.policyfailures
helpviewer_keywords: policy errors, code analysis
ms.assetid: d1f221cd-68c0-4277-9397-b76ad0dbae77
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 268940f39d3d74e7dd701f9c458d7dd08ff6c1f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="code-analysis-policy-errors"></a>Erreurs de stratégie d’analyse du code
Les erreurs suivantes se produisent si la stratégie d’analyse du code n’est pas satisfaite à l’archivage :  
  
 **Les paramètres d’analyse du Code pour un ou plusieurs projets ne sont pas compatibles avec la stratégie d’analyse du Code.**  
  
 Les besoins d’analyse de code vérification le contrôle de code source de projet équipe n’a pas été remplie pour un ou plusieurs projets de code. Cette erreur peut être causée par une ou plusieurs des conditions suivantes :  
  
1.  Analyse du code n’est pas activée sur la build pour tous les projets dans la solution.  
  
2.  La règle locale pour le projet dans Visual Studio a moins restrictive **Action** définition à la règle de projet d’équipe définie, par exemple, une règle est définie sur **Action**=**erreur**  sur le serveur a son **Action** la valeur **avertissement** ou **aucun** dans la règle définie en cours d’exécution dans Visual Studio).  
  
3.  L’ensemble spécifié dans Visual Studio de règles ne contient pas toutes les règles qui sont spécifiés dans la règle spécifiée dans la stratégie de vérification de l’analyse du Code pour le projet d’équipe.  
  
 **Échec de la stratégie d’analyse du Code. {0} projet comporte des erreurs ou la génération n’est pas à jour.**  
  
 La génération contient des erreurs ou les erreurs ont été résolues, mais l’analyse du code n’a pas été effectuée après la correction.  
  
 **Échec de l’archivage. La stratégie d’analyse du Code requiert que vous archivez via Visual Studio avec une solution ouverte.**  
  
 La stratégie d’analyse du code requiert que tous les fichiers en cours d’archivage doivent être dans la solution actuellement ouverte. Pour corriger cette erreur, ouvrez la solution qui contient le fichier à être archivé.  
  
 **Tous les fichiers dans l’archivage en attente se trouvent dans la solution actuellement ouverte.**  
  
 La stratégie d’analyse du code requiert que tous les fichiers en cours d’archivage doivent être dans la solution actuellement ouverte. Cette erreur est générée lorsqu’il existe une solution ouverte, mais certains fichiers dans la vue « archivage en attente » ne font pas partie de la solution actuellement ouverte. Pour corriger cette erreur, ouvrez la solution qui contient le fichier à être archivé.  
  
 **La version de '{0}' n’est pas correcte. Le nom fort spécifié dans la stratégie est « {{1} ».**  
  
 Cette erreur s’applique aux projets .NET. Un fichier .dll de règle requise par la stratégie d’analyse du code existe sur l’ordinateur local, mais la version/clé publique ne correspond pas. Pour corriger cette erreur, le créateur de la stratégie doit mettre à jour les fichiers .dll dans *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  répertoire sur leur ordinateur.  
  
 **assembly '{0}' spécifiée dans la stratégie n’existe pas.**  
  
 Cette erreur s’applique aux projets .NET. Une règle requise par la stratégie d’analyse du code n’a pas de dll correspondante installée sur l’ordinateur client. Pour corriger cette erreur, le créateur de la stratégie doit mettre à jour la dll dans *C:\Program Files\Microsoft Visual Studio 8\Team Tools\Static Analysis Tools\FxCop\Rules\\*  répertoire sur leur ordinateur.  
  
 **Paramètres de règle de {0} de projet ne sont pas en conformité avec la stratégie d’analyse du Code.**  
  
 Cette erreur s’applique aux projets .NET. Les paramètres de règles de code managé ne sont pas aussi strictes que la stratégie requiert. Pour corriger cette erreur, le paramètre client doit être identiques ou plus stricte que l’exigence de la stratégie sur le serveur.  
  
 **Analyse du code n’est pas activée pour la configuration active. Basculez vers {0} de la configuration et générer {{1} du projet avant d’archiver.**  
  
 Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la configuration active n’a pas d’analyse du code activée, mais il existe au moins une analyse du code activée.  
  
 **Vous devez activer l’analyse du Code pour les fichiers binaires managés dans les propriétés du projet {0} et build avant l’archivage.**  
  
 Cette erreur s’applique aux [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] applications .NET. La stratégie nécessite que l’analyse du code managé à exécuter, mais il n’est pas activée dans le projet en cours sur le client.  
  
 **Vous devez activer l’analyse du Code dans les propriétés du projet {0} et build avant l’archivage.**  
  
 Cette erreur s’appliquée aux [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projets et aux projets Web. La stratégie nécessite que l’analyse du code managé à exécuter, mais il n’est pas activée dans le projet en cours sur le client.  
  
 **Vous devez activer l’analyse du Code C/C++ dans les propriétés du projet {0} et build avant l’archivage.**  
  
 Cette erreur s’applique aux projets non managés. La stratégie d’analyse du code nécessite l’analyse du Code pour C/C++, mais il n’est pas activée dans le projet en cours sur le client.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs d’application d’analyse du code](../code-quality/code-analysis-application-errors.md)