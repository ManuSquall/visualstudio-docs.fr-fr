---
title: Mise en route avec le débogueur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d30c45c0601b6e291604275fdc9cfc4f3b5def6d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948177"
---
# <a name="getting-started-with-the-debugger"></a>Prise en main du débogueur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogueur Visual Studio est facile à utiliser dans n'importe quel langage. Nous allons montrer ici comment déboguer un programme C# simple, mais vous pouvez appliquer les mêmes étapes à du code dans d'autres langages, comme C++ et JavaScript.  
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a> Déboguer un projet de base en C#  
 Nous allons commencer par une application de console C# simple (**fichier / nouveau / projet**, puis sélectionnez **Visual C#** , puis sélectionnez **Application Console**). Si vous n’avez jamais travaillé avec Visual Studio, consultez [procédure pas à pas : Créer une Application Simple](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). Le **Main** méthode ajoute 1 à une variable entière 10 fois juste et affiche le résultat sur la console :  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    for (int i = 1; i <= 10; i++)  
    {  
        testInt += 1;  
    }  
    Console.WriteLine(testInt);  
}  
```  
  
 Générez ce code dans le **déboguer** configuration. Cette configuration est définie par défaut. Pour plus d’informations sur les configurations, consultez [présentation des Configurations de Build](../ide/understanding-build-configurations.md).  
  
 Exécutez ce code dans le débogueur en cliquant sur **déboguer / démarrer le débogage** (ou **Démarrer** sur la barre d’outils, ou **F5**). L’application doit se fermer presque immédiatement : vous ne pouvez donc pas savoir réellement si quelque chose a été affiché dans la fenêtre de console.  
  
 Vous pouvez arrêter l'exécution suffisamment longtemps pour voir la fenêtre de console en définissant un point d'arrêt, puis en passant à une exécution pas à pas. Pour définir un point d’arrêt, placez votre curseur dans le `Console.WriteLine` de ligne et cliquez sur **déboguer / nouveau point d’arrêt / point d’arrêt de la fonction**, ou cliquez simplement dans la marge gauche de la même ligne. Le point d'arrêt doit se présenter comme suit :  
  
 ![Définissez un point d’arrêt](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Pour plus d’informations sur les points d’arrêt, consultez [à l’aide des points d’arrêt](../debugger/using-breakpoints.md).  
  
##  <a name="BKMK_Inspect_Variables"></a> Inspecter des Variables  
 Débogage souvent implique la recherche des variables qui ne contiennent pas les valeurs que vous souhaitez à un moment donné. Nous allons montrer quelques-unes des méthodes que vous pouvez inspecter les variables.  
  
 Redémarrez le débogage. L'exécution s'arrête avant l'exécution du code `Console.WriteLine`. Vous pouvez provoquer son exécution en pas à pas détaillé à l’avance (cliquez sur **déboguer / Over** ou **F10**). Dans ce cas vous auriez pouvez choisir **pas à pas détaillé** (**F11**) et obtenir le même résultat ; nous expliquerons la différence par la suite. La ligne avec la dernière accolade de la méthode doit être passée en jaune. Regardez la fenêtre de console. Vous devriez voir **10**.  
  
 Vous pouvez pointer sur le **testInt** variable pour afficher la valeur actuelle dans une bulle.  
  
 ![DBG&#95;Basics&#95;Data&#95;Tips](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Juste en dessous de la fenêtre de code, vous devez voir le **automatique**, **variables locales**, et **espion** windows. Ces fenêtres montrent les valeurs des variables au moment de l'exécution. Les deux le **automatique** et **variables locales** windows show **testInt** avec la valeur **10**.  
  
 ![Fenêtre automatique lors du débogage](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Pour plus d’informations sur ces fenêtres, consultez [automatique et variables locales Windows](../debugger/autos-and-locals-windows.md).  
  
 Voyons comment la valeur de la variable change à mesure que nous avançons dans le programme. Définir un point d’arrêt sur la `testInt += 1;` de ligne et redémarrez le débogage. Vous devez voir que **testInt** dans le **variables locales** et **automatique** windows est **0**, et **je** est **1**. Si vous continuez le débogage (**déboguer / continuer**, ou **continuer** sur la barre d’outils, ou **F5**), vous pouvez voir que la valeur de **testInt** modifications apportées aux **1**, puis **2**, et ainsi de suite. Lorsque vous recevez assez de regarder ces changements, supprimez le point d’arrêt (**déboguer / basculer le point d’arrêt**, ou cliquez dessus dans la marge) et continuer le débogage. Si vous souhaitez supprimer tous les points d’arrêt, cliquez sur **déboguer / supprimer tous les points d’arrêt**, ou **CTRL + MAJ + F9**, puis cliquez sur **Oui** sur la boîte de dialogue qui vous demande **voulez-vous vous souhaitez supprimer tous les points d’arrêt ?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Pas à pas détaillé et principal des appels de fonction  
 Vous pouvez exécuter du code dans la débogueur instruction par instruction (**pas à pas détaillé**) ou vous pouvez exécuter du code pendant que le débogueur ignore les fonctions (**pas à pas principal**) pour accéder rapidement au code que vous êtes plus intéressé () code de fonction est toujours exécuté). Vous pouvez basculer entre les deux méthodes dans la même session de débogage.  
  
 Pour voir la différence entre **pas à pas détaillé** et **pas à pas principal**, nous devons ajouter une méthode qui est appelée par une autre méthode. Ajoutez une méthode à l'application C# et appelez-la à partir de la méthode Main. Le code doit se présenter comme ceci :  
  
```csharp  
static void Main(string[] args)  
{  
    Method1();  
    Console.WriteLine("end");  
}  
  
private static void Method1()  
{  
    Console.WriteLine("in Method1");  
}  
```  
  
 Définissez un point d'arrêt sur l'appel de `Method1();` dans la méthode Main et démarrez le débogage. Lorsque l’exécution s’arrête, cliquez sur **déboguer / pas à pas détaillé** (ou **pas à pas détaillé** sur la barre d’outils, ou **F11**). L'exécution s'arrête à nouveau à la première accolade dans Method1() :  
  
 ![Pas à pas détaillé dans le code](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Arrêter le débogage et démarrez à nouveau et lorsque l’exécution s’arrête au point d’arrêt, cliquez sur **déboguer / Over** (ou **pas à pas principal** sur la barre d’outils, ou **F10**). L'exécution s'arrête à nouveau sur `Console.WriteLine("end");`.  
  
 Si vous souhaitez en savoir plus sur la navigation dans le code avec le débogueur, consultez [naviguer dans le Code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md).
