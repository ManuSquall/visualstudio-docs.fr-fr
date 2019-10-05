---
title: "CA2001 : Évitez d'appeler des méthodes susceptibles de poser des problèmes"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 95209067f3821b6446b64dc7990e189720d20cea
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233191"
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001 : Évitez d'appeler des méthodes susceptibles de poser des problèmes

|||
|-|-|
|TypeName|AvoidCallingProblematicMethods|
|CheckId|CA2001|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un membre appelle une méthode potentiellement dangereuse ou problématique.

## <a name="rule-description"></a>Description de la règle

Évitez d’effectuer des appels de méthode inutiles et potentiellement dangereux. Une violation de cette règle se produit lorsqu’un membre appelle l’une des méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Appel de GC. La collecte peut affecter de manière significative les performances de l’application et est rarement nécessaire. Pour plus d’informations, consultez l’entrée de blog [morceaux performance de Rico Mariani](http://go.microsoft.com/fwlink/?LinkId=169256) sur MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. suspend et thread. Resume ont été dépréciés en raison de leur comportement imprévisible.  Utilisez d’autres classes dans <xref:System.Threading> l’espace de noms <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>telles que <xref:System.Threading.Semaphore>, et, pour synchroniser des threads ou protéger des ressources.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|La méthode DangerousGetHandle présente un risque de sécurité, car elle peut retourner un handle qui n’est pas valide. Consultez les <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> méthodes et pour plus d’informations sur l’utilisation de la méthode DangerousGetHandle en toute sécurité.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Ces méthodes peuvent charger des assemblys à partir d’emplacements inattendus. Par exemple, consultez les billets [de blog .NET CLR notes de Suzanne Cook et LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) et en [choisissant un contexte de liaison](http://go.microsoft.com/fwlink/?LinkId=164451) pour obtenir des informations sur les méthodes qui chargent les assemblys.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) Ole32|Au moment où le code utilisateur commence à s’exécuter dans un processus managé, il est trop tard pour appeler CoSetProxyBlanket de manière fiable. Le common language runtime (CLR) effectue des actions d’initialisation qui peuvent empêcher les utilisateurs de P/Invoke de se dérouler correctement.<br /><br /> Si vous devez appeler CoSetProxyBlanket pour une application managée, nous vous recommandons de démarrer le processus à l’aide d’un exécutable deC++code natif (), d’appeler CoSetProxyBlanket dans le code natif, puis de démarrer votre application de code managé dans le processus. (Veillez à spécifier un numéro de version du Runtime).|

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez ou remplacez l’appel à la méthode dangereuse ou problématique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous devez supprimer les messages de cette règle uniquement quand aucune alternative à la méthode problématique n’est disponible.

## <a name="see-also"></a>Voir aussi

- [Avertissements liés à la fiabilité](../code-quality/reliability-warnings.md)