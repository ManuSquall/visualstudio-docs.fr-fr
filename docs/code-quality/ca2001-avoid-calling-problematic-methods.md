---
title: "CA2001 : Évitez d'appeler des méthodes susceptibles de poser des problèmes"
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8053a3317e75959f030a0df6e11ead3bed17f02e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
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
 Éviter d’effectuer des appels de méthode inutiles et potentiellement dangereux.

 Une violation de cette règle se produit lorsqu’un membre appelle une des méthodes suivantes.

|Méthode|Description|
|------------|-----------------|
|<xref:System.GC.Collect%2A?displayProperty=fullName>|Appel de GC. Collect peut affecter considérablement les performances des applications et est rarement nécessaire. Pour plus d’informations, consultez la [Performance Tidbits de Rico Mariani](http://go.microsoft.com/fwlink/?LinkId=169256) entrée de blog sur MSDN.|
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread.Suspend et Thread.Resume ont été déconseillées en raison de leur comportement imprévisible.  Utilisez d’autres classes dans le <xref:System.Threading> espace de noms, tel que <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, <xref:System.Threading.Mutex>, et <xref:System.Threading.Semaphore> pour synchroniser des threads ou protéger des ressources.|
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|La méthode DangerousGetHandle compromet la sécurité, car elle peut retourner un handle qui n’est pas valide. Consultez le <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> et <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> méthodes pour plus d’informations sur l’utilisation de la méthode DangerousGetHandle en toute sécurité.|
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Ces méthodes peuvent charger des assemblys à partir d’emplacements inattendus. Par exemple, consultez les billets de blog .NET CLR Notes de Suzanne Cook [LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) et [en choisissant un contexte de liaison](http://go.microsoft.com/fwlink/?LinkId=164451) sur le site Web MSDN pour plus d’informations sur les méthodes qui chargent des assemblys.|
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|Au moment où le code utilisateur commence à s’exécuter dans un processus managé, il est trop tard pour appeler de manière fiable CoSetProxyBlanket. Le common language runtime (CLR) effectue les actions de l’initialisation qui peuvent empêcher les utilisateurs P/Invoke de réussir.<br /><br /> Si vous devez appeler CoSetProxyBlanket pour une application managée, nous vous recommandons de démarrer le processus à l’aide d’un fichier exécutable en code natif (C++), appelez CoSetProxyBlanket en code natif et puis démarrez votre application de code managé dans le processus. (Veillez à spécifier un numéro de version du runtime.)|

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez ou remplacez l’appel à la méthode dangereuse ou problématique.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous devez supprimer les messages de cette règle uniquement quand aucune alternative à la méthode problématique n’est disponibles.

## <a name="see-also"></a>Voir aussi
 [Avertissements liés à la fiabilité](../code-quality/reliability-warnings.md)