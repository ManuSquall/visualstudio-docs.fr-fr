---
title: 'CA2139 : Les méthodes transparentes ne peuvent pas utiliser l’attribut HandleProcessCorruptingExceptions | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a77100ce43480c797b15d28699923e4370a22c48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139 : Les méthodes transparentes ne peuvent pas utiliser l'attribut HandleProcessCorruptingExceptions
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|  
|CheckId|CA2139|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode transparente est marquée avec le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attribut.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle déclenche toute méthode transparente qui essaie de gérer un exception qui endommage à l’aide de processus le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> attribut. Un exception qui endommage de processus est une classification d’exception CLR version 4.0 des exceptions tel <xref:System.AccessViolationException>. L'attribut HandleProcessCorruptedStateExceptionsAttribute peut uniquement être utilisé par des méthodes critiques de sécurité et sera ignoré s'il s'applique à une méthode transparente. Pour gérer les exceptions qui endommagent un processus, cette méthode doit être critique de sécurité ou critique sécurisé.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> d’attribut, ou marquez la méthode avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> attribut.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, une méthode transparente est marquée avec le <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> d’attribut et échouera la règle. La méthode doit également être marquée avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> attribut.  
  
 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]