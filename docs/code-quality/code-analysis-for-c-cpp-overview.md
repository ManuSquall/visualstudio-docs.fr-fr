---
title: "Vue d&#39;ensemble de l&#39;analyse du code&#160;C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "directives #pragma, analyse du code"
  - "annotations, analyse du code"
  - "intégration de génération, analyse du code"
  - "C, analyse du code"
  - "C/C++ (analyse du code)"
  - "C++, analyse du code"
  - "stratégies d'archivage, analyse du code"
  - "analyse du code (outil)"
  - "analyse du code, C/C++"
  - "ligne de commande, analyse du code"
  - "IDE, analyse du code"
  - "pragma (directive), analyse du code"
ms.assetid: 81f0c9e8-f471-4de5-aac4-99db336a8809
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Vue d&#39;ensemble de l&#39;analyse du code&#160;C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'outil d'analyse du code C\/C\+\+ fournit aux développeurs des informations sur d'éventuelles erreurs présentes dans leur code source C\/C\+\+.  Les erreurs de codage courantes signalées par l'outil sont les dépassements de mémoire tampon, la mémoire désinitialisée, les déréférencements du pointeur null et les fuites de mémoire et de ressources.  
  
## Intégration IDE \(environnement de développement intégré\)  
 Pour faciliter l'utilisation de l'outil d'analyse par les développeurs, il est totalement intégré dans l'environnement IDE de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Pendant le processus de génération, tous les avertissements générés pour le code source apparaissent dans la fenêtre Liste d'erreurs.  Vous pouvez naviguer jusqu'à code source à l'origine de l'avertissement, et consulter des informations supplémentaires sur la cause du problème et d'éventuelles solutions.  
  
## Prise en charge de \#pragma  
 Les développeurs peuvent utiliser la directive `#pragma` pour traiter les avertissements comme des erreurs, activer ou désactiver des avertissements et en supprimer pour des lignes de code individuelles.  Pour plus d’informations, consultez [How to: Enable and Disable Code Analysis for Specific C\/C\+\+ Warnings](http://msdn.microsoft.com/fr-fr/910b8518-71f1-4b2e-b012-70647795642a).  
  
## Prise en charge des annotations  
 Les annotations améliorent l'exactitude de l'analyse de code.  Elles donnent des informations supplémentaires sur les conditions pre\- et post\- des paramètres de fonction et les types de retour.  Pour plus d'informations, consultez [Comment : spécifier des informations de code supplémentaire en utilisant \_\_analysis\_assume](../Topic/How%20to:%20Specify%20Additional%20Code%20Information%20by%20Using%20__analysis_assume.md)  
  
## Exécution de l'outil d'analyse dans le cadre de la stratégie d'archivage  
 Vous pouvez exiger que tous les archivages de code source appliquent certaines stratégies.  En particulier, il convient de s'assurer que cette analyse a été exécutée dans le cadre de la génération locale la plus récente.  Pour plus d'informations sur l'activation d'une stratégie d'archivage de l'analyse du code, consultez [Création et utilisation de stratégies d'archivage de l'analyse du code](../code-quality/creating-and-using-code-analysis-check-in-policies.md)  
  
## Intégration de Team Build  
 Vous pouvez utiliser les fonctionnalités intégrées du système de génération pour exécuter l'outil d'analyse du code dans le cadre du processus de génération [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)].  Pour plus d’informations, consultez [Générer l'application](../Topic/Build%20the%20application.md).  
  
## Prise en charge de la ligne de commande  
 En plus de l'intégration complète dans l'environnement de développement, les développeurs peuvent utiliser l'outil d'analyse à partir de la ligne de commande, comme le montre l'exemple suivant :  
  
 `C:\>cl /analyze Sample.cpp`