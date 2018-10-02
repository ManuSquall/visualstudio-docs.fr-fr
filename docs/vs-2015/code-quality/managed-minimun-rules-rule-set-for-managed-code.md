---
title: Définir des règles des règles minimales managées pour le code managé | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cca9670f65ef517a4697fc0752c65cbafbaa3b16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500973"
---
# <a name="managed-minimun-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles minimales managées pour le code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [définir des règles des règles minimales managées pour le code managé](https://docs.microsoft.com/visualstudio/code-quality/managed-minimun-rules-rule-set-for-managed-code).  
  
Les règles minimales gérées vous concentrer sur les problèmes les plus critiques dans votre code, notamment les failles de sécurité potentielles, les blocages d’application et les autres erreurs de logique et de conception importantes. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets.  
  
|Règle|Description|  
|----------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Les types qui possèdent des champs supprimables doivent être supprimables|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Supprimez les finaliseurs vides|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Champs supprimables doivent être supprimés.|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Surchargez l’opérateur equals en remplaçant ValueType.Equals|



