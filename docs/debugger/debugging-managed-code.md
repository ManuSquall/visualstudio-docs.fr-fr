---
title: Débogage du Code managé | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging managed code
- debugging ASP.NET Web applications, managed code
- managed code, debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 227dfcf82a179a83428900f75d0b5c9b85248479
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476362"
---
# <a name="debugging-managed-code"></a>Débogage du code managé

Cette section décrit les problèmes de débogage courants et les techniques destinées aux applications managées ou aux applications écrites dans des langages qui ciblent le Common Language Runtime, tels que Visual Basic, C# et C++. Les techniques présentées ici sont d'un niveau élevé. Pour plus d’informations, consultez [à l’aide du débogueur](../debugger/debugger-basics.md).

## <a name="in-this-section"></a>Dans cette section

[Messages de diagnostic dans la fenêtre Sortie](../debugger/diagnostic-messages-in-the-output-window.md)  
Décrit la <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.Trace> classes, avec lequel vous pouvez écrire des messages d’exécution pour le **sortie** fenêtre. Ces classes contiennent des méthodes de sortie qui permettent la génération d'informations sans interrompre l'exécution et la génération d'informations avec interruption de l'exécution si une condition spécifique échoue.

[Assertions dans du code managé](../debugger/assertions-in-managed-code.md)  
Décrit des assertions en code managé, qui testent les conditions que vous spécifiez comme arguments aux méthodes `Assert`. De plus, cette rubrique fournit des exemples de code, des informations sur l'utilisation des méthodes de classe  <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.Trace>, des considérations des versions Debug et Release de code, les effets secondaires, les arguments assert, la personnalisation du comportement d'assertion et les fichiers de configuration.

[Instructions Stop en Visual Basic](../debugger/stop-statements-in-visual-basic.md)  
Décrit l'instruction `Stop`, qui propose une alternative à la définition d'un point d'arrêt. Un exemple de code, ainsi que les comparaisons entre les instructions `Stop` et `End` et les instructions `Stop` et `Assert` sont également fournis.

[Procédure pas à pas : débogage d’un Windows Form](../debugger/walkthrough-debugging-a-windows-form.md)  
Fournit des instructions étape par étape pour créer un Windows Form et le déboguer. Un Windows Form, composant standard d'une application Windows managée, est l'une des applications managées les plus courantes. Cette procédure pas à pas utilise Visual C# et Visual Basic, mais les techniques de création d'un formulaire Windows avec C++ sont généralement similaires.

[Débogage de la méthode OnStart](../debugger/how-to-debug-the-onstart-method.md)  
Fournit des exemples de code pour vous permettre de déboguer la méthode `OnStart` d'un service Windows managé. Pour déboguer la méthode `OnStart` d'un service Windows, vous devez ajouter quelques lignes de code pour simuler le service.

[Débogage en Mode mixte](../debugger/debugging-mixed-mode-applications.md)  
Présente les applications de débogage en mode mixte. Désigne toutes les applications qui combinent du code natif avec du code managé.

[Erreur : le débogage est impossible, car un débogueur du noyau est activé sur le système](../debugger/error-debugging-isn-t-possible-because-a-kernel-debugger-is-enabled-on-the-system.md)  
Décrit un message d’erreur qui se produit si vous essayez de déboguer du code managé sur un [!INCLUDE[win7](../debugger/includes/win7_md.md)], [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)], [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], [!INCLUDE[Win2kFamily](../code-quality/includes/win2kfamily_md.md)], ou le système de Windows NT qui a été démarré en mode débogage.

[Optimisation et débogage JIT](../debugger/jit-optimization-and-debugging.md)  
Décrit les effets de l'optimisation JIT sur le débogage.

[Débogage LINQ et DLINQ](../debugger/debugging-linq.md)  
Décrit les techniques de débogage des requêtes LINQ.

[Procédure pas à pas : débogage d’une application parallèle](../debugger/walkthrough-debugging-a-parallel-application.md)  
Décrit comment utiliser le **tâches parallèles** et **piles parallèles** fenêtres pour déboguer une application parallèle.

## <a name="related-sections"></a>Rubriques connexes

[IntelliTrace](../debugger/intellitrace.md) rechercher des bogues plus rapidement et plus faciles en enregistrant l’historique d’exécution de votre application avec IntelliTrace. Parcourez en mode pas à pas (en avant et en arrière) les événements et appels enregistrés pour examiner l'état de votre application à certains points clés dans le temps. Déboguez votre code sans définir un grand nombre de points d'arrêt ni redémarrer votre application fréquemment. Nécessite Visual Studio Enterprise.

[Suivi et instrumentation d’applications](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
Décrit le traçage, qui vous permet de contrôler l'exécution de votre application lorsque celle-ci s'exécute, et l'instrumentation, qui implique de placer des instructions de traçage à des endroits stratégiques de votre code. Cette rubrique fournit également des liens vers une introduction à l'instrumentation et au traçage, aux commutateurs de trace, aux écouteurs de la trace, au code de traçage dans une application, à l'ajout d'instructions de traçage au code d'une application et à la compilation conditionnelle avec <xref:System.Diagnostics.Debug> et <xref:System.Diagnostics.Trace>.

[/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute)  
Décrit une option de l’éditeur de liens ajoute <xref:System.Diagnostics.DebuggableAttribute> à du code écrit avec C++. Cet attribut est nécessaire pour utiliser les fonctionnalités de débogage telles que l’attachement avec C++.

[Débogage des Applications Windows Service](/dotnet/framework/windows-services/how-to-debug-windows-service-applications)  
Fournit des considérations pour le débogage d'applications de service Windows, y compris la configuration, l'attachement au processus, le débogage de code dans la méthode `OnStart` du service et de code dans la méthode Main, la définition de points d'arrêt, et l'utilisation du Gestionnaire de contrôle des services pour démarrer, arrêter, interrompre et continuer votre service.

[Débogage et profilage](/dotnet/framework/debug-trace-profile/index)  
Décrit le débogage des applications .NET Framework et les exigences de configuration.

[Débogage de scripts et Applications Web](../debugger/debugging-web-applications-and-script.md)  
Décrit les problèmes et techniques de débogage courants relatifs au débogage de scripts et d'applications Web.

[Quelles sont les nouveautés du débogueur dans Visual Studio 2015](../debugger/what-s-new-for-the-debugger-in-visual-studio.md)  
Description des nouvelles fonctionnalités de débogage ajoutées à cette version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

[Page d’accueil de débogage](../debugger/debugger-feature-tour.md)  
Fournit des liens vers des sections plus vastes de la documentation relative au débogage. Les informations présentées sont les suivantes : nouveautés du débogueur, paramètres et préparation, points d'arrêt, gestion des exceptions, fonctionnalité Modifier & Continuer, débogage de code managé, débogage de projets Visual C++, débogage COM et ActiveX, débogage de DLL, débogage SQL et les références relatives à l'interface utilisateur.

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : Débogage Windows Forms personnalisés des contrôles au moment du Design](/dotnet/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time)
[sécurité du débogueur](../debugger/debugger-security.md)
[débogage dans Visual Studio](../debugger/index.md) 
 [ Visite guidée des fonctionnalités du débogueur](../debugger/debugger-feature-tour.md)