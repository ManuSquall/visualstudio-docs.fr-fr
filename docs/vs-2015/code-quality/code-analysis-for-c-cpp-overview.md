---
title: Analyse du code pour une vue d’ensemble de C / C++ | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
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
caps.latest.revision: 27
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c6764e39d55ebe2ce11776035f25d6fdf69be081
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505772"
---
# <a name="code-analysis-for-cc-overview"></a>Vue d'ensemble de l'analyse du code C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [analyse du Code pour C/C++ Overview](https://docs.microsoft.com/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
L'outil d'analyse du code C/C++ fournit aux développeurs des informations sur d'éventuelles erreurs présentes dans leur code source C/C++. Les erreurs de codage courantes signalées par l'outil sont les dépassements de mémoire tampon, la mémoire désinitialisée, les déréférencements du pointeur null et les fuites de mémoire et de ressources.  
  
## <a name="ide-integrated-development-environment-integration"></a>Intégration IDE (environnement de développement intégré)  
 Pour le rendre naturelle pour les développeurs à utiliser l’outil d’analyse, il est entièrement intégré dans le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Pendant le processus de génération, tous les avertissements générés pour le code source apparaissent dans la liste d’erreurs. Vous pouvez accéder au code source qui a provoqué l’avertissement, et vous pouvez afficher des informations supplémentaires sur la cause et les solutions possibles du problème.  
  
## <a name="pragma-support"></a>prise en charge de #pragma  
 Les développeurs peuvent utiliser le `#pragma` directive pour traiter les avertissements comme des erreurs ; activer ou désactiver les avertissements et supprimer des avertissements pour des lignes de code. Pour plus d’informations, consultez [Comment : activer et désactiver l’analyse du Code pour les avertissements C/C++ spécifiques](http://msdn.microsoft.com/en-us/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Prise en charge de l’annotation  
 Annotations améliorent la précision de l’analyse du code. Annotations fournissent des informations supplémentaires sur les conditions de pré- et post-paramètres de fonction et les types de retour. Pour plus d’informations, consultez [Comment : spécifier les informations du Code supplémentaire en utilisant __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Exécutez l’outil d’analyse dans le cadre de la stratégie d’archivage  
 Vous souhaiterez peut-être nécessitent que tous les source code archivages respectent certaines stratégies. En particulier, vous souhaitez vous assurer que l’analyse a été exécutée dans le cadre de la dernière génération locale. Pour plus d’informations sur l’activation d’une stratégie d’archivage de l’analyse du code, consultez [création et à l’aide de Code Analysis stratégies d’archivage](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Intégration de Team Build  
 Vous pouvez utiliser les fonctionnalités intégrées du système de génération pour exécuter l’outil d’analyse de code dans le cadre de la [!INCLUDE[esprtfs](../includes/esprtfs-md.md)] du processus de génération. Pour plus d’informations, consultez l’article [Générer l’application](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Prise en charge de ligne de commande  
 En plus de l’intégration complète au sein de l’environnement de développement, les développeurs peuvent également utiliser l’outil d’analyse à partir de la ligne de commande, comme indiqué dans l’exemple suivant :  
  
 `C:\>cl /analyze Sample.cpp`



