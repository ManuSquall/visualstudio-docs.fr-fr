---
title: "CA1504 : Vérifier les noms de champs trompeurs | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dc1317380eab4a63a7c60557fbec258485768885
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504 : Vérifier les noms de champs trompeurs
|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|Category|Microsoft.Maintainability|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Le nom d’un champ d’instance commence par « s_ » ou le nom d’un `static` (`Shared` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) du champ commence par « m_ ».  
  
## <a name="rule-description"></a>Description de la règle  
 Les noms de champs qui commencent par « s_ » sont associés à des données statiques par de nombreux utilisateurs. De même, les noms de champs qui commencent par « m_ » sont associés à des données d’instance (membre). Pour le code plus facile à maintenir, noms doivent suivre les conventions communément utilisées.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, renommez le champ à l’aide du préfixe approprié. Vous pouvez également accorder le champ avec le suffixe actuel en ajoutant ou supprimant le `static` modificateur.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.