---
title: Résolution des problèmes liés à l’analyse du code | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: b8d17fcaec0034d2803f769cc5595416f5d56de8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505806"
---
# <a name="troubleshooting-code-analysis-issues"></a>Résolution des problèmes liés à l'analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [résolution des problèmes analyse du Code](https://docs.microsoft.com/visualstudio/code-quality/troubleshooting-code-analysis-issues).  
  
Cette rubrique contient des informations de résolution des problèmes suivants liés à l’analyse du code Visual Studio.  
  
-   [Des modifications apportées à un ensemble de règles de Visual Studio 2010 ne sont pas répercutées dans les versions antérieures de Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Des modifications apportées à un ensemble de règles de Visual Studio 2010 ne sont pas répercutées dans les versions antérieures de Visual Studio  
 Quand vous créez un ensemble de règles dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] qui contient un ensemble de règles enfant, une modification de cet ensemble de règles peut ne pas être appliquée dans les exécutions de l’analyse du code sur des ordinateurs qui utilisent une version antérieure de Visual Studio. Pour résoudre ce problème, vous devez forcer une réécriture de l’ensemble de règles parent, qui est l’ensemble de règles contenant l’ensemble de règles enfant.  
  
1.  Ouvrez l’ensemble de règles parent dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
2.  Faites une modification, comme ajouter ou supprimer une règle, puis enregistrez l’ensemble de règles.  
  
3.  Rouvrez l’ensemble de règles, annulez la modification, puis réenregistrez l’ensemble de règles.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de la qualité des applications](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Utilisation d’ensembles de règles pour regrouper des règles d’analyse du code](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)



