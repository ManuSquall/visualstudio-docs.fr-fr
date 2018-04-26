---
title: Vue d'ensemble de l'analyse du code C/C++
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 71b9652333913a6b101da9669824a9adb21943af
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="code-analysis-for-cc-overview"></a>Analyse du code pour une vue d’ensemble de C/C++

L'outil d'analyse du code C/C++ fournit aux développeurs des informations sur d'éventuelles erreurs présentes dans leur code source C/C++. Les erreurs de codage courantes signalées par l'outil sont les dépassements de mémoire tampon, la mémoire désinitialisée, les déréférencements du pointeur null et les fuites de mémoire et de ressources.

## <a name="ide-integrated-development-environment-integration"></a>Intégration IDE (environnement de développement intégré)
 Pour faciliter aux développeurs d’utiliser l’outil d’analyse, il est entièrement intégré dans le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Pendant le processus de génération, tous les avertissements générés pour le code source s’affichent dans la liste d’erreurs. Vous pouvez accéder au code source qui a provoqué l’avertissement, et vous pouvez afficher des informations supplémentaires sur la cause et les solutions possibles du problème.

## <a name="pragma-support"></a>#pragma prise en charge
 Les développeurs peuvent utiliser le `#pragma` directive pour considérer les avertissements comme des erreurs ; activer ou désactiver des avertissements et supprimer les avertissements pour des lignes de code. Pour plus d’informations, consultez [Comment : définir des propriétés d’analyse de Code pour les projets C/C++ ](how-to-set-code-analysis-properties-for-c-cpp-projects.md).

## <a name="annotation-support"></a>Prise en charge de l’annotation
 Annotations améliorent la précision de l’analyse du code. Annotations fournissent des informations supplémentaires sur les conditions antérieurs et postérieur sur les paramètres de fonction et les types de retour. Pour plus d’informations, consultez [Comment : spécifier les informations de Code supplémentaire en utilisant __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)

## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Exécuter l’outil d’analyse dans le cadre de la stratégie d’archivage
 Vous souhaiterez peut-être nécessitent que tous les source code archivages respectent certaines stratégies. En particulier, vous souhaitez vous assurer que l’analyse a été exécutée dans le cadre de la dernière build locale. Pour plus d’informations sur l’activation d’une stratégie d’archivage de l’analyse du code, consultez [création et à l’aide de Code analyse stratégies d’archivage](../code-quality/creating-and-using-code-analysis-check-in-policies.md)

## <a name="team-build-integration"></a>Intégration de Team Build
 Vous pouvez utiliser les fonctionnalités intégrées du système de génération pour exécuter l’outil d’analyse du code dans le cadre de la [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] processus de génération. Pour plus d’informations, consultez [Build et mise en production](/vsts/build-release/index).

## <a name="command-line-support"></a>Prise en charge de ligne de commande
 En plus de l’intégration complète dans l’environnement de développement, les développeurs peuvent également utiliser l’outil d’analyse à partir de la ligne de commande, comme indiqué dans l’exemple suivant :

 `C:\>cl /analyze Sample.cpp`

## <a name="see-also"></a>Voir aussi

[Analyse de la qualité du pilote à l’aide des outils d’analyse du Code](/windows-hardware/drivers/develop/analyzing-driver-quality-by-using-code-analysis-tools)
[l’analyse du Code pour les avertissements de pilotes](/windows-hardware/drivers/devtest/prefast-for-drivers-warnings)