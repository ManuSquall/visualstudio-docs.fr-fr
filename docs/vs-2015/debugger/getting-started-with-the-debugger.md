---
title: Prise en main avec le débogueur | Microsoft Docs
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
ms.openlocfilehash: e093abd5e836bcb7ee236979c00d574a07ecfd3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202313"
---
# <a name="getting-started-with-the-debugger"></a>Prise en main du débogueur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogueur Visual Studio est facile à utiliser dans n'importe quel langage. Nous allons montrer ici comment déboguer un programme C# simple, mais vous pouvez appliquer les mêmes étapes à du code dans d'autres langages, comme C++ et JavaScript.  
  
## <a name="debug-a-basic-c-project"></a><a name="BKMK_Start_debugging_a_VS_project"></a> Déboguer un projet C# de base  
 Commençons par une application console C# simple (**fichier/nouveau/projet**, puis sélectionnez **Visual C#** , puis sélectionnez **application console**). Si vous n’avez jamais travaillé avec Visual Studio, consultez [procédure pas à pas : création d’une application simple](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md). La méthode **main** ajoute simplement 1 à une variable entière 10 fois et imprime le résultat sur la console :  
  
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
  
 Générez ce code dans la configuration **Debug** . Cette configuration est définie par défaut. Pour plus d’informations sur les configurations, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).  
  
 Exécutez ce code dans le débogueur en cliquant sur déboguer **/Démarrer le débogage** (ou **Démarrer** dans la barre d’outils, ou **F5**). L’application doit se fermer presque immédiatement : vous ne pouvez donc pas savoir réellement si quelque chose a été affiché dans la fenêtre de console.  
  
 Vous pouvez arrêter l'exécution suffisamment longtemps pour voir la fenêtre de console en définissant un point d'arrêt, puis en passant à une exécution pas à pas. Pour définir un point d’arrêt, placez votre curseur sur la `Console.WriteLine` ligne et cliquez sur **Déboguer/nouveau point d’arrêt/point d’arrêt sur fonction**, ou cliquez simplement dans la marge de gauche sur la même ligne. Le point d'arrêt doit se présenter comme suit :  
  
 ![Définir un point d’arrêt](../debugger/media/getstartedbreakpoint.png "GetStartedBreakpoint")  
  
 Pour plus d’informations sur les points d’arrêt, consultez [utilisation de points d’arrêt](../debugger/using-breakpoints.md).  
  
## <a name="inspect-variables"></a><a name="BKMK_Inspect_Variables"></a> Inspecter les variables  
 Le débogage implique souvent la recherche de variables qui ne contiennent pas les valeurs que vous attendez à un point particulier. Nous allons vous montrer quelques-unes des façons dont vous pouvez inspecter les variables.  
  
 Redémarrez le débogage. L'exécution s'arrête avant l'exécution du code `Console.WriteLine`. Vous pouvez l’exécuter en effectuant un pas à pas détaillé (cliquez sur **Déboguer/pas à pas principal** ou **F10**). Dans ce cas, vous pourriez avoir choisi **pas à pas détaillé** (**F11**) et obtenu le même résultat. Nous expliquerons la différence ultérieurement. La ligne avec la dernière accolade de la méthode doit être passée en jaune. Regardez la fenêtre de console. Vous devez voir **10**.  
  
 Vous pouvez pointer sur la variable **testInt** pour afficher la valeur actuelle dans une bulle d’informations.  
  
 ![&#95;de base de DBG&#95;des conseils sur les&#95;de données](../debugger/media/dbg-basics-data-tips.png "DBG_Basics_Data_Tips")  
  
 Juste en dessous de la fenêtre de code, vous devriez voir les fenêtres **automatique**, **variables locales**et **Espion** . Ces fenêtres montrent les valeurs des variables au moment de l'exécution. Les fenêtres **automatique** et **variables locales** affichent **testInt** avec une valeur de **10**.  
  
 ![Fenêtre Automatique lors du débogage](../debugger/media/getstartedwindows.png "GetStartedWindows")  
  
 Pour plus d’informations sur ces fenêtres, consultez les [fenêtres automatique et variables locales](../debugger/autos-and-locals-windows.md).  
  
 Voyons comment la valeur de la variable change à mesure que nous avançons dans le programme. Définissez un point d’arrêt sur la `testInt += 1;` ligne, puis redémarrez le débogage. Vous devez voir que **testInt** dans les **fenêtres variables locales** et **automatique** a la **valeur 0**, et **que i** est égal à **1**. Quand vous poursuivez le débogage (**Déboguer/continuer**, ou **Continuer** dans la barre d’outils, ou **F5**), vous pouvez voir que la valeur de **testInt** passe à **1**, puis à **2**, et ainsi de suite. Lorsque vous n’avez plus besoin d’examiner ces modifications, supprimez le point d’arrêt (**Déboguer/basculer le point d’arrêt**ou cliquez dessus dans la marge), puis poursuivez le débogage. Si vous souhaitez supprimer tous les points d’arrêt, cliquez sur **Déboguer/supprimer tous les points d’arrêt**, ou sur **CTRL + MAJ + F9**, puis cliquez sur **Oui** dans la boîte de dialogue qui vous demande si **vous souhaitez supprimer tous les points d’arrêt ?**.  
  
## <a name="stepping-into-and-over-function-calls"></a>Pas à pas détaillé et principal des appels de fonction  
 Vous pouvez exécuter le code dans l’instruction (**pas à pas**détaillé) du débogueur ou vous pouvez exécuter le code pendant que le débogueur ignore les fonctions (**pas à pas principal**) pour accéder rapidement au code qui vous intéresse (le code de fonction est toujours exécuté). Vous pouvez basculer entre les deux méthodes dans la même session de débogage.  
  
 Pour voir la différence entre **pas à pas** détaillé et **pas à pas principal**, nous devons ajouter une méthode qui est appelée par une autre méthode. Ajoutez une méthode à l'application C# et appelez-la à partir de la méthode Main. Le code doit se présenter comme ceci :  
  
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
  
 Définissez un point d'arrêt sur l'appel de `Method1();` dans la méthode Main et démarrez le débogage. Lorsque l’exécution s’arrête, cliquez sur **Déboguer/pas à pas** détaillé (ou **pas à pas** détaillé dans la barre d’outils, ou **F11**). L'exécution s'arrête à nouveau à la première accolade dans Method1() :  
  
 ![Pas à pas détaillé dans le code](../debugger/media/getstartedstepinto.png "GetStartedStepInto")  
  
 Arrêtez le débogage et redémarrez et, lorsque l’exécution s’arrête au point d’arrêt, cliquez sur **Déboguer/pas à pas principal** (ou **pas à pas principal** dans la barre d’outils, ou **F10**). L'exécution s'arrête à nouveau sur `Console.WriteLine("end");`.  
  
 Si vous souhaitez en savoir plus sur la navigation dans le code avec le débogueur, consultez [navigation dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md).
