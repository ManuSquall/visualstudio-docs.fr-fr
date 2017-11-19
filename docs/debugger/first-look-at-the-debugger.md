---
title: "Prise en main du débogueur dans Visual Studio | Documents Microsoft"
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: 0b3138c4-b840-446a-a15c-10ed8e2dd050
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68eb471f1db42b60114c2a14745ba4771b640c0d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="get-started-with-the-visual-studio-debugger"></a>Prise en main du débogueur Visual Studio
Le débogueur Visual Studio est facile à utiliser dans n'importe quel langage. Nous allons montrer ici comment déboguer un programme c# simple, mais vous pouvez appliquer les mêmes étapes pour le code dans d’autres langages tels que C++ et JavaScript.

Pour visionner une vidéo montrant des fonctionnalités similaires, consultez [mise en route avec le débogueur](https://www.youtube.com/watch?v=FtGCi5j30YU&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=6).
  
##  <a name="BKMK_Start_debugging_a_VS_project"></a>Déboguer un projet c# de base  
 Nous allons commencer par une application de console c# simple (**fichier > Nouveau > projet**, puis sélectionnez **Visual C#** , puis **Application Console**). Si vous n’avez jamais travaillé avec Visual Studio, consultez [procédure pas à pas : création d’une Application Simple](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). Le **Main** méthode simplement ajoute 1 à une variable entière 10 fois et affiche le résultat sur la console :  
  
```CSharp  
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
  
 Exécutez ce code dans le débogueur en cliquant sur **Déboguer > Démarrer le débogage** (ou **Démarrer** sur la barre d’outils, ou **F5**). L’application doit se fermer presque immédiatement, donc vous ne pouvez pas savoir réellement si quelque chose a été affiché dans la fenêtre de Console.  
  
 Vous pouvez arrêter l'exécution suffisamment longtemps pour voir la fenêtre de console en définissant un point d'arrêt, puis en passant à une exécution pas à pas. Pour définir un point d’arrêt, placez le curseur dans la `Console.WriteLine` de ligne et cliquez sur **Déboguer > Nouveau point d’arrêt > point d’arrêt de la fonction**, ou cliquez simplement dans la marge de gauche de la même ligne. Le point d'arrêt doit se présenter comme suit :  
  
 ![Définir un point d’arrêt](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Pour plus d’informations sur les points d’arrêt, consultez [à l’aide des points d’arrêt](../debugger/using-breakpoints.md).  
  
##  <a name="BKMK_Inspect_Variables"></a>Inspecter des Variables  
 Débogage souvent implique la recherche des variables qui ne contiennent pas les valeurs que vous attendez à un moment donné. Nous allons montrer les méthodes que vous pouvez inspecter des variables.  
  
 Redémarrez le débogage. L'exécution s'arrête avant l'exécution du code `Console.WriteLine`. Vous pouvez provoquer qu’il s’exécute en passant (cliquez sur **Déboguer > pas à pas principal** ou **F10**). Dans ce cas vous auriez pu choisir **pas à pas détaillé** (**F11**) et obtenir le même résultat ; nous expliquerons la différence plus tard. La ligne avec la dernière accolade de la méthode doit être passée en jaune. Regardez la fenêtre de console. Vous devez voir **10**.  
  
 Vous pouvez pointer sur le **testInt** variable pour afficher la valeur actuelle dans une info-bulle.  
  
 ![DBG &#95; Principes de base &#95; données &#95; Conseils](../debugger/media/dbg_basics_data_tips.png "DBG_Basics_Data_Tips")  
  
 Juste en dessous de la fenêtre de code, vous devez voir le **automatique**, **variables locales**, et **espion** windows. Ces fenêtres montrent les valeurs des variables au moment de l'exécution. Les deux le **automatique** et **variables locales** windows afficher **testInt** avec la valeur **10**.  
  
 ![Automatique (fenêtre) lors du débogage](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Pour plus d’informations sur ces fenêtres, consultez [les fenêtres variables locales et automatique](../debugger/autos-and-locals-windows.md).  
  
 Nous allons voir comment la valeur de la variable change à mesure que nous avançons dans le programme. Définir un point d’arrêt sur la `testInt += 1;` de ligne et redémarrez le débogage. Vous devez voir que **testInt** dans les **variables locales** et **automatique** windows est **0**, et **i** est **1**. Lorsque vous reprenez le débogage (**Déboguer > continuer**, ou **continuer** sur la barre d’outils, ou **F5**), vous pouvez voir que la valeur de **testInt** modifications apportées à **1**, puis **2**, et ainsi de suite. Lorsque vous obtenez assez de regarder ces changements, supprimez le point d’arrêt (**Déboguer > point d’arrêt**, ou cliquez dessus dans la marge) et continuer le débogage. Si vous souhaitez supprimer tous les points d’arrêt, cliquez sur **Déboguer > supprimer tous les points d’arrêt**, ou **CTRL + MAJ + F9**, puis cliquez sur **Oui** sur la boîte de dialogue qui vous demande **faire Voulez-vous supprimer les points d’arrêt ?** .  
  
## <a name="stepping-into-and-over-function-calls"></a>Pas à pas détaillé et principal des appels de fonction  
 Vous pouvez exécuter du code dans la débogueur instruction par instruction (**pas à pas détaillé**) ou vous pouvez exécuter le code pendant que le débogueur ignore les fonctions (**pas à pas principal**) pour accéder rapidement au code que vous êtes davantage intéressé de () code de fonction est toujours exécutée). Vous pouvez basculer entre les deux méthodes dans la même session de débogage.  
  
 Pour voir la différence entre **pas à pas détaillé** et **pas à pas principal**, nous devons ajouter une méthode qui est appelée par une autre méthode. Ajoutez une méthode à l'application C# et appelez-la à partir de la méthode Main. Le code doit se présenter comme ceci :  
  
```CSharp  
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
  
 Définissez un point d'arrêt sur l'appel de `Method1();` dans la méthode Main et démarrez le débogage. Lorsque l’exécution s’arrête, cliquez sur **Déboguer > pas à pas détaillé** (ou **pas à pas détaillé** sur la barre d’outils, ou **F11**). L'exécution s'arrête à nouveau à la première accolade dans Method1() :  
  
 ![Pas à pas détaillé dans le code](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Arrêter le débogage et lancez à nouveau lorsque l’exécution s’arrête au point d’arrêt, cliquez sur **Déboguer > pas à pas principal** (ou **pas à pas principal** sur la barre d’outils, ou **F10**). L'exécution s'arrête à nouveau sur `Console.WriteLine("end");`.  
  
 Si vous souhaitez plus d’informations sur la navigation dans le code avec le débogueur, consultez [naviguer dans le Code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md).