---
title: Inspecter une exception-Visual Studio | Microsoft Docs
ms.date: 1/18/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- exception helper, debugger, exception
- debugging [Visual Studio], exception helper, Examine an exception
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e2157b55915f82e79dfdac5d300046850a93879
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600304"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Inspecter une exception à l’aide de l’assistance d’exception 

La gestion des exceptions est un problème courant, quelle que soit la technologie ou le niveau d’expertise. Il peut s’agir d’une expérience frustrante pour déterminer pourquoi des exceptions sont à l’origine de problèmes dans votre code. Quand vous déboguez une exception dans Visual Studio, nous souhaitons réduire cette frustration en vous fournissant des informations d’exception pertinentes pour vous aider à déboguer votre problème plus rapidement.

![Assistance d’exception](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Suspendre à l’exception
Quand le débogueur s’arrête sur une exception, une icône d’erreur d’exception apparaît à droite de cette ligne de code. Une assistance d’exception non modale s’affiche à côté de l’icône d’exception.

![Assistance d’exception en regard d’une ligne de code](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Inspecter les informations sur les exceptions
Vous pouvez lire instantanément le type d’exception et le message d’exception dans le programme d’assistance de l’exception, et si l’exception a été levée ou non. Vous pouvez inspecter et afficher les propriétés de l’objet exception en cliquant sur le lien **afficher les détails** .

## <a name="analyze-null-references"></a>Analyser les références null
À compter de Visual Studio 2017, pour le code .net et C/C++, quand vous appuyez `NullReferenceException` sur un ou un `AccessViolation` , vous voyez des informations d’analyse null dans le programme d’assistance de l’exception. L’analyse s’affiche sous forme de texte sous le message d’exception. Dans l’illustration ci-dessous, les informations s’affichent sous la forme «**s** a la valeur null ».

![Analyse null de l’assistance d’exception](media/debugger-exception-helper-default.png)


> [!NOTE]
> L’analyse de référence null dans le code managé requiert .NET version 4.6.2. Les analyses NULL ne sont actuellement pas prises en charge pour les plateforme Windows universelle (UWP) et toutes les autres applications .NET Core. Elle est uniquement disponible pendant le débogage de code qui n’a pas d’optimisations de code juste-à-temps (JIT).

## <a name="configure-exception-settings"></a>Configurer les paramètres d’exception 
Vous pouvez configurer le débogueur pour qu’il s’arrête lorsqu’une exception du type actuel est levée à partir de la section des **paramètres d’exception** du programme d’assistance de l’exception. Si le débogueur est suspendu à une exception levée, vous pouvez utiliser la case à cocher pour désactiver l’interruption sur ce type d’exception lorsqu’il est levé à l’avenir. Si vous ne souhaitez pas arrêter cette exception particulière quand elle est levée dans ce module particulier, cochez la case en regard du nom du module sous **sauf si elle est levée à partir de :** dans la fenêtre **paramètres d’exception** . 

## <a name="inspect-inner-exceptions"></a>Inspecter les exceptions internes 
Si l’exception contient des exceptions internes ([innerException](/dotnet/api/system.exception.innerexception), vous pouvez les afficher dans le programme d’assistance de l’exception. Si plusieurs exceptions sont présentes, vous pouvez naviguer entre elles à l’aide des flèches gauche et droite affichées au-dessus de la pile des appels.

![Assistance d’exception avec l’exception interne](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Inspecter les exceptions levées à nouveau
Dans les cas où une exception s’est produite, `thrown` l’assistance d’exception affiche la pile des appels de la première fois que l’exception a été levée. Si l’exception a été levée plusieurs fois, seule la pile des appels de l’exception d’origine est affichée.

![Exception Helper avec exceptions levées à nouveau](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Partager une session de débogage avec Live Share
À partir de l’assistance d’exception, vous pouvez démarrer une session de [Live share](/visualstudio/liveshare/) en utilisant le lien **démarrer la session Live share...**. Toute personne qui rejoint la session de Live Share peut voir l’assistance de l’exception, ainsi que toutes les autres informations de débogage.