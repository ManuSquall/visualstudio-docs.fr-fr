---
title: "Analyse du code pour une vue d’ensemble de C/C++ | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- annotations, code analysis
- build integration, code analysis
- C/C++ code analysis
- IDE, code analysis
- pragma directive, code analysis
- code analysis, C/C++
- code analysis tool
- command line, code analysis
- C++, code analysis
- check-in policies, code analysis
- '#pragma directives, code analysis'
- C, code analysis
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 55b1f4061d408187525c255e4ab12c3fe93eb60e
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="code-analysis-for-cc-overview"></a>Vue d'ensemble de l'analyse du code C/C++
L'outil d'analyse du code C/C++ fournit aux développeurs des informations sur d'éventuelles erreurs présentes dans leur code source C/C++. Les erreurs de codage courantes signalées par l'outil sont les dépassements de mémoire tampon, la mémoire désinitialisée, les déréférencements du pointeur null et les fuites de mémoire et de ressources.  
  
## <a name="ide-integrated-development-environment-integration"></a>Intégration IDE (environnement de développement intégré)  
 Pour faciliter aux développeurs d’utiliser l’outil d’analyse, il est entièrement intégré dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Pendant le processus de génération, tous les avertissements générés pour le code source s’affichent dans la liste d’erreurs. Vous pouvez accéder au code source qui a provoqué l’avertissement, et vous pouvez afficher des informations supplémentaires sur la cause et les solutions possibles du problème.  
  
## <a name="pragma-support"></a>#pragma prise en charge  
 Les développeurs peuvent utiliser le `#pragma` directive pour considérer les avertissements comme des erreurs ; activer ou désactiver des avertissements et supprimer les avertissements pour des lignes de code. Pour plus d’informations, consultez [Comment : activer et désactiver l’analyse du Code pour les avertissements C/C++ spécifiques](http://msdn.microsoft.com/en-us/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Prise en charge de l’annotation  
 Annotations améliorent la précision de l’analyse du code. Annotations fournissent des informations supplémentaires sur les conditions antérieurs et postérieur sur les paramètres de fonction et les types de retour. Pour plus d’informations, consultez [Comment : spécifier les informations de Code supplémentaire en utilisant __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Exécuter l’outil d’analyse dans le cadre de la stratégie d’archivage  
 Vous souhaiterez peut-être nécessitent que tous les source code archivages respectent certaines stratégies. En particulier, vous souhaitez vous assurer que l’analyse a été exécutée dans le cadre de la dernière build locale. Pour plus d’informations sur l’activation d’une stratégie d’archivage de l’analyse du code, consultez [création et à l’aide de Code analyse stratégies d’archivage](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Intégration de Team Build  
 Vous pouvez utiliser les fonctionnalités intégrées du système de génération pour exécuter l’outil d’analyse du code dans le cadre de la [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] processus de génération. Pour plus d’informations, consultez l’article [Générer l’application](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Prise en charge de ligne de commande  
 En plus de l’intégration complète dans l’environnement de développement, les développeurs peuvent également utiliser l’outil d’analyse à partir de la ligne de commande, comme indiqué dans l’exemple suivant :  
  
 `C:\>cl /analyze Sample.cpp`