---
title: 'CA1415 : Déclarer P-appelle correctement | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfad5d5a699fda54c91e674365b65305ef7fad0d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415 : Déclarer correctement les méthodes P/Invoke
|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|Category|Microsoft.Interoperability|  
|Modification avec rupture|Sans rupture - Si P/Invoke qui déclare le paramètre ne peut pas être visible à l’extérieur de l’assembly. Avec rupture - Si P/Invoke qui déclare le paramètre est visible à l’extérieur de l’assembly.|  
  
## <a name="cause"></a>Cause  
 Un appel de méthode est déclarée de manière incorrecte.  
  
## <a name="rule-description"></a>Description de la règle  
 Une plateforme de l’appel de méthode accède à un code non managé et est définie à l’aide de la `Declare` mot clé dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Cette règle recherche actuellement des déclarations de méthode qui ciblent des fonctions Win32 présentant un pointeur vers un paramètre de structure OVERLAPPED non managé et le paramètre managé correspondant n’est pas un pointeur vers un <xref:System.Threading.NativeOverlapped?displayProperty=fullName> structure.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, déclarez correctement la plate-forme appeler la méthode.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre les méthodes qui enfreint la règle et répondent à la règle d’appel de plateforme.  
  
 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interopération avec du code non managé](/dotnet/framework/interop/index)