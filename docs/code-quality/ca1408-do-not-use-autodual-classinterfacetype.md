---
title: "CA1408 : Ne pas utiliser AutoDual ClassInterfaceType | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ad19c3fa245998d57542a5dfe1b9da0c61984626
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408 : Ne pas utiliser le paramètre AutoDual ClassInterfaceType
|||  
|-|-|  
|TypeName|DoNotUseAutoDualClassInterfaceType|  
|CheckId|CA1408|  
|Category|Microsoft.Interoperability|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type visible du modèle COM (Component Object) est marqué avec la <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribut défini sur le `AutoDual` valeur <xref:System.Runtime.InteropServices.ClassInterfaceType>.  
  
## <a name="rule-description"></a>Description de la règle  
 Les types qui utilisent une interface double permettent aux clients de se lier à une disposition d'interface spécifique. Les modifications apportées à une version future de la disposition du type ou des types de base bloquent les clients COM qui se lient à l'interface. Par défaut, si le <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> attribut n’est pas spécifié, une interface de répartition uniquement est utilisée.  
  
 Sauf mention contraire, tous les types non génériques publics sont visibles par COM ; tous les types génériques et non publics ne sont pas visibles par COM.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez la valeur de la <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> d’attribut pour le `None` valeur <xref:System.Runtime.InteropServices.ClassInterfaceType> et définissez explicitement l’interface.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle, sauf s’il est certain que la disposition du type et ses types de base ne change pas dans une future version.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une classe qui enfreint la règle et une nouvelle déclaration de la classe à utiliser une interface explicite.  
  
 [!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)  
  
 [CA1412 : Marquez les interfaces ComSource comme IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Qualification des types .NET pour l’interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Interopération avec du code non managé](/dotnet/framework/interop/index)