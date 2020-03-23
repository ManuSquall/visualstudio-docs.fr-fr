---
title: Naviguez avec le débbuggeur . Microsoft Docs
ms.custom: seodec18
ms.date: 11/12/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.execution
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dfffdf0c12ea2a8f14769f26bb40a3943579248
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302118"
---
# <a name="navigate-through-code-with-the-visual-studio-debugger"></a>Naviguez à travers le code avec le debugger Visual Studio

Le débbugger Visual Studio peut vous aider à naviguer à travers le code pour inspecter l’état d’une application et afficher son flux d’exécution. Vous pouvez utiliser des raccourcis clavier, des commandes de débocher, des points d’arrêt et d’autres fonctionnalités pour accéder rapidement au code que vous souhaitez examiner. La familiarité avec les commandes de navigation et les raccourcis de débbugger le rend plus rapide et plus facile à trouver et à résoudre les problèmes d’application.  Si c’est la première fois que vous avez essayé de déboguer du code, vous pouvez lire [Debugging pour les débutants absolus](../debugger/debugging-absolute-beginners.md) et [les techniques et les outils Debugging](../debugger/write-better-code-with-visual-studio.md) avant de passer par cet article.

## <a name="get-into-break-mode"></a>Entrez en "mode pause"

En *mode pause,* l’exécution de l’application est suspendue pendant que les fonctions, les variables et les objets restent en mémoire. Une fois que le débbuggeur est en mode pause, vous pouvez naviguer à travers votre code. Les moyens les plus courants d’entrer en mode pause rapidement est de l’un ou l’autre:

- Commencer à faire un pas de code en appuyant sur **F10** ou **F11**. Cela vous permet de trouver rapidement le point d’entrée de votre application, alors vous pouvez continuer à appuyer sur les commandes d’étape pour naviguer dans le code.

- [Exécutez à un emplacement ou une fonction spécifique,](#BKMK_Break_into_code_by_using_breakpoints_or_Break_All)par exemple, [en définissant un point d’arrêt](using-breakpoints.md) et en commençant votre application.

   Par exemple, à partir de l’éditeur de code de Visual Studio, vous pouvez utiliser la commande **Run to Cursor** pour démarrer l’application, déboguer et entrer en mode pause, puis **F11** pour naviguer dans le code.

   ![Exécuter au curseur et entrer dans le code](../debugger/media/navigate-code-code-stepping.gif "Exécuter au curseur et entrer dans le code")

Une fois en mode pause, vous pouvez utiliser une variété de commandes pour naviguer à travers votre code. Pendant votre mode de rupture, vous pouvez examiner les valeurs des variables pour rechercher des violations ou des bogues. Pour certains types de projets, vous pouvez également apporter des ajustements à l’application pendant le mode pause.

La plupart des fenêtres de débogé, comme les modules et les fenêtres **watch,** ne sont **disponibles** que lorsque le débbuggeur est fixé à votre application. Certaines caractéristiques de débbugger, telles que l’affichage des valeurs variables dans la fenêtre **Locals** ou l’évaluation des expressions dans la fenêtre **Watch,** ne sont disponibles que pendant que le débbuggeur est en pause (c’est-à-dire en mode pause).

> [!NOTE]
> Si vous vous cassez dans le code qui n’a pas de source ou de symbole (*.pdb*) fichiers chargés, le débbuggeur affiche un **fichier source non trouvé** ou **symboles non trouvés** page qui peut vous aider à trouver et charger les fichiers. Voir [Spécifier le symbole (.pdb) et les fichiers source](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Si vous ne pouvez pas charger le symbole ou les fichiers source, vous pouvez toujours débomber les instructions d’assemblage dans la fenêtre **de démontage.**

## <a name="step-through-code"></a>Exécuter le code pas à pas

Les commandes de step de débogénaire vous aident à inspecter l’état de votre application ou à en savoir plus sur son flux d’exécution.

### <a name="step-into-code-line-by-line"></a><a name="BKMK_Step_into__over__or_out_of_the_code"></a>Entrez dans le code ligne par ligne

Pour arrêter chaque instruction tout en débogage, utilisez **Debug** > **Step Into**, ou appuyez sur **F11**.

Le débbuggeur passe par des instructions de code, pas des lignes physiques. Par exemple, une clause `if` peut être écrite sur une ligne :

  ```csharp
  int x = 42;
  string s = "Not answered";
  if( int x == 42) s = "Answered!";
  ```

  ```vb
  Dim x As Integer = 42
  Dim s As String = "Not answered"
  If x = 42 Then s = "Answered!"
  ```

Cependant, lorsque vous entrez dans cette ligne, le débbuggeur traite la condition comme une étape, et la conséquence comme une autre. Dans l’exemple précédent, la condition est vraie.

Dans un appel à plusieurs fonctions imbriquées, **Pas à pas détaillé** va jusqu'à la fonction se trouvant au niveau le plus profond. Par exemple, si vous utilisez Step `Func1(Func2())` **Into** sur un appel comme `Func2`, le débbuggeur entre dans la fonction .

>[!TIP]
>Lorsque vous exécutez chaque ligne de code, vous pouvez survoler les variables pour voir leurs valeurs, ou utiliser les [fenêtres Locals](autos-and-locals-windows.md) and [Watch](watch-and-quickwatch-windows.md) pour regarder les valeurs changer. Vous pouvez également tracer visuellement la [pile d’appels](how-to-use-the-call-stack-window.md) tout en entrant dans les fonctions. (Pour Visual Studio Enterprise seulement, voir [les méthodes de carte sur la pile d’appel tout en débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)).

### <a name="step-through-code-and-skip-some-functions"></a><a name="BKMK_Step_over_Step_out"></a>Passez à travers le code et sautez certaines fonctions

Vous ne vous souciez peut-être pas d’une fonction tout en débogage, ou vous savez que cela fonctionne, comme le code de bibliothèque bien testé. Vous pouvez utiliser les commandes suivantes pour sauter le code pendant la marche de code. Les fonctions s’exécutent toujours, mais le débbuggeur saute sur eux.

|Commande de clavier|Commande du menu Déboguer|Description|
|----------------------|------------------|-----------------|
|**F10**|**Pas à pas principal**|Si la ligne actuelle contient un appel de fonction, **Step Over** exécute le code, puis suspend l’exécution à la première ligne de code après le retour de la fonction appelée.|
|**Quart de travail**+**F11**|**Pas à pas sortant**|**Step Out** continue d’exécuter le code et suspend l’exécution lorsque la fonction actuelle revient. Le débagé debugger saute à travers la fonction actuelle.|

## <a name="run-to-a-specific-location-or-function"></a><a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a>Exécuter à un endroit ou une fonction spécifique

Vous préférerez peut-être vous diriger directement vers un emplacement ou une fonction spécifique lorsque vous savez exactement quel code vous souhaitez inspecter, ou si vous savez où vous voulez commencer à débogage.

### <a name="run-to-a-breakpoint-in-code"></a>Exécuter à un point d’arrêt dans le code

Pour définir un point d’arrêt simple dans votre code, cliquez sur la marge à gauche à côté de la ligne de code où vous souhaitez suspendre l’exécution. Vous pouvez également sélectionner la ligne et appuyer sur **F9**, sélectionnez **Debug** > **Toggle Breakpoint**, ou cliquez à droite et sélectionnez **Breakpoint** > **d’insertion**de point de rupture . Le point d’arrêt apparaît comme un point rouge dans la marge gauche à côté de la ligne de code. Le débagé suspend l’exécution juste avant l’exécution de la ligne.

![Définir un point d’arrêt](../debugger/media/dbg_basics_setbreakpoint.png "Définir un point d'arrêt")

Les points d'arrêt dans Visual Studio fournissent un ensemble enrichi de fonctionnalités supplémentaires, telles que les points d'arrêt et les points de trace conditionnels. Pour plus de détails, voir [Utiliser des points d’arrêt](../debugger/using-breakpoints.md).

### <a name="run-to-a-function-breakpoint"></a>Exécuter à un point d’arrêt de la fonction

Vous pouvez dire au débbuggeur de fonctionner jusqu’à ce qu’il atteigne une fonction spécifiée. Vous pouvez spécifier la fonction par nom ou la sélectionner dans la pile des appels.

**Pour spécifier un point d’arrêt de fonction par nom**

1. Sélectionnez **Debug** > **New Breakpoint** > **Function Breakpoint**

1. Dans le dialogue **New Function Breakpoint,** tapez le nom de la fonction et sélectionnez sa langue.

   ![Nouvelle boîte de dialogue Function Breakpoint](../debugger/media/dbg_execution_newbreakpoint.png "Nouveau point d’arrêt de la fonction")

1. Sélectionnez **OK**.

Si la fonction est surchargée ou dans plus d’un namespace, vous pouvez choisir celui que vous voulez dans la fenêtre **Breakpoints.**

![Points d’arrêt de fonction surchargés](../debugger/media/dbg_execution_overloadedbreakpoints.png "Points d’arrêt de fonction surchargés")

**Pour sélectionner un point d’arrêt de fonction à partir de la pile d’appels**

1. Tout en débogage, ouvrez la fenêtre **Call Stack** en sélectionnant **Debug** > **Windows** > Call**Stack**.

1. Dans la fenêtre **Call Stack,** cliquez à droite sur une fonction et **sélectionnez Run To Cursor**, ou appuyez sur **Ctrl**+**F10**.

Pour tracer visuellement la pile d’appel, voir [les méthodes de carte sur la pile d’appel tout en débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="run-to-a-cursor-location"></a>Courir à un emplacement curseur

Pour courir à l’emplacement du curseur, dans le code source ou la fenêtre **Call Stack,** sélectionnez la ligne à laquelle vous souhaitez vous casser, cliquer à droite et sélectionner **Run To Cursor**, ou appuyez sur **Ctrl**+**F10**. Sélectionner **Run To Cursor,** c’est comme définir un point d’arrêt temporaire.

### <a name="run-to-click"></a>Exécuter jusqu’au clic

En pause dans le débbugger, vous pouvez planer au-dessus d’une déclaration dans le code source ou la fenêtre **démontage,** et sélectionnez **l’exécution Run à l’icône** de flèche verte ici. L’utilisation **de Run to Click** élimine la nécessité de définir un point d’arrêt temporaire.

![Exécuter jusqu’au clic](../debugger/media/dbg-run-to-click.png "Exécuter jusqu’au clic")

> [!NOTE]
> **Run to Click** est [!include[vs_dev15](../misc/includes/vs_dev15_md.md)]disponible à partir de .

### <a name="manually-break-into-code"></a>S'arrêter manuellement dans le code

Pour casser la prochaine ligne de code disponible dans une application en cours d’exécution, sélectionnez **Debug** > **Break All**, ou appuyez sur **Ctrl**+**Alt**+**Break**.

## <a name="move-the-pointer-to-change-the-execution-flow"></a><a name="BKMK_Set_the_next_statement_to_execute"></a>Déplacez le pointeur pour modifier le flux d’exécution

Pendant que le débbuggeur est mis en pause, une pointe de flèche jaune dans la marge du code source ou de la fenêtre **de démontage** marque l’emplacement de la déclaration suivante à exécuter. Vous pouvez modifier la prochaine instruction pour exécuter en déplaçant cette pointe de flèche. Vous pouvez sauter sur une partie du code, ou revenir à une ligne précédente. Déplacer le pointeur est utile pour des situations telles que sauter une section de code qui contient un bogue connu.

 ![Déplacer le pointeur](../debugger/media/dbg_basics_example3.gif "Déplacer le pointeur")

Pour modifier la prochaine instruction à exécuter, le débbuggeur doit être en mode pause. Dans le code source ou la fenêtre **de démontage,** faites glisser la pointe de flèche jaune à une ligne différente, ou cliquez à droite sur la ligne que vous souhaitez exécuter ensuite et sélectionnez **Set Next Statement**.

Le compteur du programme saute directement au nouvel emplacement, et les instructions entre les anciens et les nouveaux points d’exécution ne sont pas exécutées. Toutefois, si vous déplacez le point d’exécution vers l’arrière, les instructions d’intervention ne sont pas annulées.

>[!CAUTION]
>- Le déplacement de l'instruction suivante vers une autre fonction ou portée entraîne généralement une altération de la pile des appels, provoquant une erreur ou exception d'exécution. Si vous tentez de déplacer l'instruction suivante vers une autre portée, le débogueur ouvre une boîte de dialogue avec un avertissement et vous donne une occasion d'annuler l'opération.
>- En Visual Basic, vous ne pouvez pas déplacer l'instruction suivante à une autre portée ou fonction.
>- En C++ natif, si les contrôles d'exécution sont activés, la définition de l'instruction suivante peut provoquer la levée d'une exception lorsque l'exécution atteint la fin de la méthode.
>- Lorsque Modifier &amp; Continuer est activé, la commande **Définir l'instruction suivante** échoue si vous avez apporté des modifications qui ne peuvent pas être remappées immédiatement par Modifier &amp; Continuer. Par exemple, cela peut se produire si vous avez modifié le code contenu dans un bloc catch. Lorsque cela se produit, un message d’erreur vous indique que l’opération n’est pas prise en charge.
>- Dans le code géré, vous ne pouvez pas déplacer la déclaration suivante si :
>   - L'instruction suivante se trouve dans une méthode différente de celle de l'instruction actuelle.
>   - Debugging a été lancé par Just-In-Time débogage.
>   - Une pile d’appels se détend est en cours.
>   - Une exception System.StackOverflowException ou System.Threading.ThreadAbortException a été levée.

## <a name="debug-non-user-code"></a><a name="BKMK_Restrict_stepping_to_Just_My_Code"></a>Code non utilisateur Debug

Par défaut, le débbugger tente de déboquer uniquement votre code d’application en permettant un paramètre appelé *Just My Code*. Pour plus de détails sur le fonctionnement de cette fonctionnalité pour différents types de projets et les langues, et comment vous pouvez la personnaliser, voir [Just My Code](../debugger/just-my-code.md).

Pour examiner le code-cadre, le code de bibliothèque tiers ou les appels système pendant le débogage, vous pouvez désactiver Just My Code. Dans **Tools** (ou **Debug**) > **Options** > **Debugging**, effacer la case à cocher Enable Just My **Code.** Lorsque Just My Code est désactivé, le code non utilisateur apparaît dans les fenêtres de débogénaire, et le débbuggeur peut entrer dans le code non-utilisateur.

> [!NOTE]
> Uniquement mon code n'est pas pris en charge pour les projets Smart Device.

### <a name="debug-system-code"></a>Code système Debug

Si vous avez chargé des symboles de débogage pour le code système Microsoft, et désactivé Just My Code, vous pouvez entrer dans un appel système tout comme vous pouvez tout autre appel.

Pour charger les symboles Microsoft, voir [les emplacements du symbole Configurer et les options de chargement](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#configure-symbol-locations-and-loading-options).

**Pour charger des symboles pour un composant système spécifique :**

1. Pendant que vous débugging, ouvrez la fenêtre **Modules** en sélectionnant des**modules****Windows** >  **Debug** > , ou en appuyant sur **Ctrl**+**Alt**+**U**.

1. Dans la fenêtre **Modules,** vous pouvez savoir quels modules ont des symboles chargés dans la colonne **Statut du symbole.** Cliquez à droite sur le module pour lequel vous souhaitez charger des symboles et sélectionnez **les symboles de charge .**

## <a name="step-into-properties-and-operators-in-managed-code"></a><a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Effectuer un pas à pas détaillé dans des propriétés et des opérateurs au sein du code managé
 Par défaut, le débogueur effectue un pas à pas principal sur les propriétés et les opérateurs dans le code managé. Dans la plupart des cas, cela fournit une meilleure expérience de débogage. Pour permettre d’entrer dans des propriétés ou des opérateurs, choisissez **Debug** > **Options**. Sur la page **Debugging** > **General,** effacez **l’étape sur les propriétés et les opérateurs (géré uniquement)** case à cocher.

## <a name="see-also"></a>Voir aussi
- [Qu’est-ce que le débogage ?](../debugger/what-is-debugging.md)
- [Techniques et outils de débogage](../debugger/write-better-code-with-visual-studio.md)
- [Premier regard sur le débogage](../debugger/debugger-feature-tour.md)
