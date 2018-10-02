---
title: 'Exemple d’extension Excel : classe ActionFilter | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5e6aff4a57dfb84760ceb4513e06d063c01a5af0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504763"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Exemple d'extension Excel : classe ActionFilter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [exemple d’Extension Excel : classe ActionFilter](https://docs.microsoft.com/visualstudio/test/sample-excel-extension-actionfilter-class).  
  
Cette classe interne étend la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter> et représente un filtre pour les actions de test sur un élément [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
## <a name="simple-properties"></a>Propriétés simples  
 Ces propriétés en lecture seule permettent au développeur de spécifier comment ce filtre d’action de test doit être exécuté par le framework de test codé de l’interface utilisateur. Par exemple, la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A> fournit le nom du filtre d’action. D’autres propriétés obtiennent le <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> du filtre d’action, le <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A> et le nom <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A> pour les actions de test qui sont filtrées par ce filtre d’action de test. D’autres indiquent s’il faut <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> et également si l’action de test est <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>.  
  
## <a name="processrule-method"></a>ProcessRule, méthode  
 Cette méthode est appelée par le framework de test codé de l’interface utilisateur et exécute le filtre sur le <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> fourni. Cette substitution particulière supprime une action permettant de choisir une cellule avec la souris quand l’action suivante de la pile envoie des séquences de touches à la cellule. Elle retourne ensuite `false`.  
  
## <a name="private-methods"></a>Méthodes privées  
 La méthode `IsLeftClick` détermine si l’action fournie représente un clic gauche de souris. La méthode `AreActionsOnSameExcelCell` détermine si deux actions fournies sont exécutées sur la même cellule dans Excel.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



