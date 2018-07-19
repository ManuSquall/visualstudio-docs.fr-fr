---
title: "CA2205 : Utilisez des équivalents managés de l'API Win32"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d964cdbe94822fc6156e25320e723cd10fe7d853
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31919962"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205 : Utilisez des équivalents managés de l'API Win32
|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un appel de méthode est définie et une méthode avec la fonctionnalité équivalente existe dans le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] bibliothèque de classes.

## <a name="rule-description"></a>Description de la règle
 Un appel de méthode est utilisée pour appeler une fonction DLL non managée et est définie à l’aide de la <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attribut, ou le `Declare` clé en Visual Basic. Une méthode non managé défini de manière incorrecte peut entraîner des exceptions runtime en raison de problèmes tels qu’une fonction incorrectement, un mappage de types de données de valeur paramètres et de retour et des spécifications de champs incorrects, tels que la convention d’appel et le caractère erronée ensemble. S’il est disponible, il est généralement d’erreur plus simple et moins sujet à appeler la méthode managée équivalente à to définir et appeler la méthode non managée directement. Appel d’une plateforme invoke (méthode) peut également entraîner des problèmes de sécurité supplémentaires qui doivent être résolus.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez l’appel à la fonction non managée avec un appel à son équivalent managé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle si la méthode de remplacement suggérée ne fournit pas les fonctionnalités nécessaires.

## <a name="example"></a>Exemple
 L’exemple suivant montre une plateforme appeler la définition de méthode qui enfreint la règle. En outre, les appels à la plate-forme appeler la méthode et la méthode managée équivalente sont affichés.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Règles associées
 [CA1404 : Appeler GetLastError immédiatement après P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060 : Déplacer P/Invoke vers une classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400 : Des points d’entrée P/Invoke doivent exister.](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401 : Les P/Invoke ne doivent pas être visible](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101 : Spécifiez le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)