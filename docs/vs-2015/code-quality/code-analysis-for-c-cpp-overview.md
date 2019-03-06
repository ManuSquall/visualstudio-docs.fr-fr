---
title: Vue d’ensemble de l’analyse du code pour C-C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
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
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: bc84b3f89aa819755a689a0798aea7fbb8147510
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54805629"
---
# <a name="code-analysis-for-cc-overview"></a>Vue d'ensemble de l'analyse du code C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'outil d'analyse du code C/C++ fournit aux développeurs des informations sur d'éventuelles erreurs présentes dans leur code source C/C++. Les erreurs de codage courantes signalées par l'outil sont les dépassements de mémoire tampon, la mémoire désinitialisée, les déréférencements du pointeur null et les fuites de mémoire et de ressources.  
  
## <a name="ide-integrated-development-environment-integration"></a>Intégration IDE (environnement de développement intégré)  
 Pour permettre aux développeurs d’utiliser l’outil d’analyse de façon naturelle, celui-ci est entièrement intégré à l’IDE [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Durant le processus de génération, tous les avertissements générés pour le code source s’affichent dans la liste d’erreurs. Vous pouvez accéder au code source à l’origine de l’avertissement, et afficher des informations supplémentaires sur la cause et les solutions possibles du problème.  
  
## <a name="pragma-support"></a>Prise en charge de #pragma  
 Les développeurs peuvent utiliser la directive `#pragma` pour traiter les avertissements comme des erreurs, activer ou désactiver les avertissements et supprimer les avertissements liés à des lignes de code individuelles. Pour plus d'informations, voir [Procédure : Activez et désactivez l’analyse du code pour des avertissements C/C++ spécifiques](http://msdn.microsoft.com/910b8518-71f1-4b2e-b012-70647795642a).  
  
## <a name="annotation-support"></a>Prise en charge des annotations  
 Les annotations améliorent la précision de l’analyse du code. Les annotations fournissent des informations supplémentaires sur les conditions préalables et postérieures des paramètres de fonction et des types de retour. Pour plus d'informations, voir [Procédure : Spécifier des informations de code supplémentaires en utilisant __analysis_assume](../code-quality/how-to-specify-additional-code-information-by-using-analysis-assume.md)  
  
## <a name="run-analysis-tool-as-part-of-check-in-policy"></a>Exécuter l’outil d’analyse dans le cadre d’une stratégie d’archivage  
 Vous pouvez être amené à imposer que tous les archivages de code source respectent certaines stratégies. En particulier, vous souhaitez vérifier que l’analyse a été exécutée en tant qu’étape de la build locale la plus récente. Pour plus d’informations sur l’activation d’une stratégie d’archivage de l’analyse du code, consultez [Création et utilisation de stratégies d’archivage de l’analyse du code](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## <a name="team-build-integration"></a>Intégration de Team Build  
 Vous pouvez utiliser les fonctionnalités intégrées du système de build pour exécuter l’outil d’analyse du code en tant qu’étape du processus de génération [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Pour plus d’informations, consultez l’article [Générer l’application](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="command-line-support"></a>Prise en charge de la ligne de commande  
 Non seulement les développeurs bénéficient d’une intégration complète de l’outil d’analyse dans l’environnement de développement, mais ils peuvent également l’utiliser à partir de la ligne de commande, comme indiqué dans l’exemple suivant :  
  
 `C:\>cl /analyze Sample.cpp`
