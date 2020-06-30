---
title: 'CA2001 : Évitez d’appeler les méthodes problématiques | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba64c27cde5f335f32cca362417078a5c9ed13e3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538578"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001 : Évitez d'appeler des méthodes susceptibles de poser des problèmes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Category|Microsoft. fiabilité|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un membre appelle une méthode potentiellement dangereuse ou problématique.

## <a name="rule-description"></a>Description de la règle
 Évitez d’effectuer des appels de méthode inutiles et potentiellement dangereux.

 Une violation de cette règle se produit lorsqu’un membre appelle l’une des méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Appel de GC. La collecte peut affecter de manière significative les performances de l’application et est rarement nécessaire. Pour plus d’informations, consultez l’entrée de blog [performance morceaux de Rico Mariani](https://docs.microsoft.com/archive/blogs/ricom/when-to-call-gc-collect) sur MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. suspend et thread. Resume ont été dépréciés en raison de leur comportement imprévisible.  Utilisez d’autres classes dans l' <xref:System.Threading> espace de noms, telles que <xref:System.Threading.Monitor> , <xref:System.Threading.Mutex> et <xref:System.Threading.Semaphore> pour synchroniser des threads ou protéger des ressources.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|La méthode DangerousGetHandle présente un risque de sécurité, car elle peut retourner un handle qui n’est pas valide. Consultez les <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> méthodes et <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> pour plus d’informations sur l’utilisation de la méthode DangerousGetHandle en toute sécurité.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Ces méthodes peuvent charger des assemblys à partir d’emplacements inattendus. Par exemple, consultez le blog .NET CLR notes de Suzanne Cook et les publications de l’article [LoadFile](https://docs.microsoft.com/archive/blogs/suzcook/loadfile-vs-loadfrom) et du site Web MSDN pour obtenir des informations sur les méthodes de [chargement des assemblys](https://docs.microsoft.com/archive/blogs/suzcook/choosing-a-binding-context) .|
|[CoSetProxyBlanket](https://msdn.microsoft.com/library/ms692692.aspx) (ole32)<br /><br /> [CoInitializeSecurity](https://msdn.microsoft.com/library/ms693736.aspx) (ole32)|Au moment où le code utilisateur commence à s’exécuter dans un processus managé, il est trop tard pour appeler CoSetProxyBlanket de manière fiable. Le common language runtime (CLR) effectue des actions d’initialisation qui peuvent empêcher les utilisateurs de P/Invoke de se dérouler correctement.<br /><br /> Si vous devez appeler CoSetProxyBlanket pour une application managée, nous vous recommandons de démarrer le processus à l’aide d’un exécutable de code natif (C++), d’appeler CoSetProxyBlanket dans le code natif, puis de démarrer votre application de code managé dans le processus. (Veillez à spécifier un numéro de version du Runtime).|

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez ou remplacez l’appel à la méthode dangereuse ou problématique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous devez supprimer les messages de cette règle uniquement quand aucune alternative à la méthode problématique n’est disponible.

## <a name="see-also"></a>Voir aussi
 [Avertissements de fiabilité](../code-quality/reliability-warnings.md)
