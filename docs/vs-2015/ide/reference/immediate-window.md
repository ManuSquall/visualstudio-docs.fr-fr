---
title: Fenêtre Exécution | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 87f8cd822dcd67ff7837dcaa31e47c23e0a0550b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203669"
---
# <a name="immediate-window"></a>Exécution (fenêtre)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
La fenêtre **Exécution** est utilisée pour déboguer et évaluer des expressions, exécuter des instructions, imprimer les valeurs des variables, etc. Elle vous permet d’entrer des expressions qui doivent être évaluées ou exécutées par le langage de développement lors du processus de débogage. Pour afficher la fenêtre **Exécution**, ouvrez un projet à modifier, puis choisissez **Fenêtres** dans le menu **Déboguer** et sélectionnez **Exécution**, ou appuyez sur Ctrl+Alt+I.  
  
 Vous pouvez utiliser cette fenêtre pour émettre des commandes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] individuelles. Parmi les commandes disponibles, `EvaluateStatement` peut être utilisée pour assigner des valeurs aux variables. La fenêtre **Exécution** prend également en charge IntelliSense.  
  
## <a name="displaying-the-values-of-variables"></a>Affichage des valeurs de variables  
 Cette fenêtre peut être particulièrement utile lors du débogage d’une application. Par exemple, pour vérifier la valeur d’une variable `varA`, vous pouvez utiliser la [commande Imprimer](../../ide/reference/print-command.md) :  
  
```  
>Debug.Print varA  
```  
  
 Le point d’interrogation (?) est un alias pour `Debug.Print` et cette commande peut donc également s’écrire comme suit :  
  
```  
>? varA  
```  
  
 Les deux versions de cette commande retournent la valeur de la variable `varA`.  
  
> [!NOTE]
>  Pour émettre une commande [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dans la fenêtre **Exécution**, vous devez faire précéder la commande d’un signe supérieur à (>). Pour entrer plusieurs commandes, basculez vers la fenêtre **Commande**.  
  
## <a name="design-time-expression-evaluation"></a>Évaluation des expressions au moment du design  
 Vous pouvez utiliser la fenêtre **Exécution** pour exécuter une fonction ou une sous-routine au moment du design.  
  
#### <a name="to-execute-a-function-at-design-time"></a>Pour exécuter une fonction au moment du design  
  
1.  Copiez le code suivant dans une application console [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] :  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MyFunction(5)  
        End Sub  
  
        Function MyFunction(ByVal input as Integer) As Integer  
            Return input * 2  
        End Function  
  
    End Module  
    ```  
  
2.  Dans le menu **Déboguer**, cliquez sur **Fenêtres**, puis sur **Exécution**.  
  
3.  Tapez `?MyFunction(2)` dans la fenêtre **Exécution** et appuyez sur Entrée.  
  
     La fenêtre **Exécution** exécute `MyFunction` et affiche `4`.  
  
 Si la fonction ou la sous-routine contient un point d’arrêt, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] arrête l’exécution à ce point. Vous pouvez ensuite utiliser les fenêtres du débogueur pour examiner l’état de votre programme. Pour plus d’informations, consultez [Procédure pas à pas : débogage au moment du design](../../debugger/walkthrough-debugging-at-design-time.md).  
  
 Vous ne pouvez pas utiliser l’évaluation des expressions au moment du design dans les types de projet qui requièrent le démarrage d’un environnement d’exécution, notamment les projets [!INCLUDE[trprVSTOshort](../../includes/trprvstoshort-md.md)], projets web, projets Smart Device et projets SQL.  
  
### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Évaluation des expressions au moment du design dans les solutions à projets multiples  
 Lors de l’établissement du contexte pour l’évaluation des expressions au moment du design, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fait référence au projet actuellement sélectionné dans l’Explorateur de solutions. Si aucun projet n’est sélectionné dans l’Explorateur de solutions, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] tente alors d’évaluer la fonction par rapport au projet de démarrage. Si la fonction ne peut pas être évaluée dans le contexte actuel, un message d’erreur s’affiche. Si vous essayez d’évaluer une fonction dans un projet qui n’est pas le projet de démarrage pour la solution et que vous recevez une erreur, essayez de sélectionner le projet dans l’Explorateur de solutions et tentez à nouveau l’évaluation.  
  
## <a name="entering-commands"></a>Entrée de commandes  
 Vous devez entrer le signe supérieur à (>) lors de l’émission de commandes [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dans la fenêtre **Exécution**. Utilisez les touches de direction HAUT et BAS pour faire défiler les commandes précédemment émises.  
  
|Tâche|Solution|Exemple|  
|----------|--------------|-------------|  
|Évaluer une expression.|Faites précéder l’expression d’un point d’interrogation (?).|`? a+b`|  
|En mode Exécution, passer temporairement en mode Commande (pour exécuter une seule commande).|Entrez la commande en la faisant précéder du signe supérieur à (>).|`>alias`|  
|Basculer vers la fenêtre Commande.|Entrez la commande `cmd` dans la fenêtre en la faisant précéder du signe supérieur à (>).|`>cmd`|  
|Revenir à la fenêtre Exécution.|Entrez la commande `immed` dans la fenêtre sans le signe supérieur à (>).|`immed`|  
  
## <a name="mark-mode"></a>Mode Marque  
 Quand vous cliquez sur n’importe quelle ligne précédente dans la fenêtre **Exécution**, vous passez automatiquement en mode Marque. Cela vous permet de sélectionner, de modifier et de copier le texte de commandes précédentes comme vous le feriez dans n’importe quel éditeur de texte, et de les coller dans la ligne active.  
  
## <a name="the-equals--sign"></a>Signe égal (=)  
 La fenêtre utilisée pour entrer la commande `EvaluateStatement` détermine si un signe égal (=) est interprété comme un opérateur de comparaison ou comme un opérateur d’assignation.  
  
 Dans la fenêtre **Exécution**, un signe égal (=) est interprété comme un opérateur d’assignation. Ainsi, la commande  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 assigne à la variable `varA` la valeur de variable `varB`.  
  
 En revanche, dans la fenêtre **Commande**, un signe égal (=) est interprété comme un opérateur de comparaison. Vous ne pouvez pas utiliser d’opérations d’assignation dans la fenêtre **Commande**. Ainsi, si les valeurs des variables `varA` et `varB` sont différentes, la commande  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 retourne la valeur `False`.  
  
## <a name="first-chance-exception-notifications"></a>notifications d'exceptions de première chance  
 Dans certaines configurations de paramètres, les notifications d’exceptions de première chance sont affichées dans la fenêtre **Exécution**.  
  
#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Pour activer/désactiver les notifications d’exceptions de première chance dans la fenêtre Exécution  
  
1.  Dans le menu **Affichage**, cliquez sur **Autres fenêtres**, puis sur **Sortie**.  
  
2.  Cliquez avec le bouton droit sur la zone de texte de la fenêtre **Sortie** et sélectionnez ou désélectionnez **Messages d’exception**.  
  
## <a name="see-also"></a>Voir aussi  
 [Naviguer dans le code avec le débogueur](../../debugger/navigating-through-code-with-the-debugger.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Débogage dans Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Principes de base du débogueur](../../debugger/debugger-basics.md)   
 [Procédure pas à pas : débogage au moment du design](../../debugger/walkthrough-debugging-at-design-time.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Utilisation d’expressions régulières dans Visual Studio](../../ide/using-regular-expressions-in-visual-studio.md)



