---
title: Utilisez des points d’arrêt dans le débagénaire . Microsoft Docs
ms.custom: ''
ms.date: 10/28/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.location.address
- vs.debug.breakpt.constraints
- vs.debug.breakpoints.delete
- vs.debug.breakpt.location.data
- vc.breakpoints
- vs.debug.breakpt.condition
- vs.debug.breakpt.location.function
- vs.debug.breakpoints
- vs.debug.menu.insert
- vs.debug.filenames
- vs.debug.breakpt.action
- vs.debug.sourcewin.insert
- vs.debug.address
- vs.debug.data
- vs.debug.func
- vs.debug.breakpt.location.file
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6a8ee96834fc20186ba6719a7c4f377fea45d6b
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302034"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Utilisez des points d’arrêt dans le débbugger Visual Studio

Les points de rupture sont l’une des techniques de débogage les plus importantes dans la boîte à outils de votre développeur. Vous définissez des points d’arrêt où que vous vouliez interrompre l’exécution des débbuggeurs. Par exemple, vous pouvez voir l’état des variables de code ou regarder la pile d’appels à un certain point d’arrêt.  Si vous essayez de résoudre un avertissement ou un problème tout en utilisant des points d’arrêt, voir [les points de rupture Deshoot dans le debugger Visual Studio](../debugger/troubleshooting-breakpoints.md).

> [!NOTE]
> Si vous connaissez la tâche ou le problème que vous essayez de résoudre, mais vous devez savoir quel genre de point d’arrêt à utiliser, voir [Trouvez votre tâche de débogage](../debugger/find-your-debugging-task.md#pause-running-code).

## <a name="set-breakpoints-in-source-code"></a><a name="BKMK_Overview"></a>Définir les points d’arrêt dans le code source

Vous pouvez définir un point d’arrêt sur n’importe quelle ligne de code exécutable. Par exemple, dans le code C suivant, vous pouvez définir `for` un point d’arrêt `for` sur la déclaration variable, la boucle ou n’importe quel code à l’intérieur de la boucle. Vous ne pouvez pas définir un point d’arrêt sur l’espace de nom ou les déclarations de classe, ou sur la signature de la méthode.

Pour définir un point d’arrêt dans le code source, cliquez sur la marge à gauche à côté d’une ligne de code. Vous pouvez également sélectionner la ligne et appuyer sur **F9**, sélectionnez **Debug** > **Toggle Breakpoint**, ou cliquez à droite et sélectionnez **Breakpoint** > **Insert breakpoint**. Le point d’arrêt apparaît comme un point rouge dans la marge gauche.

Pour la plupart des langues, y compris le C, le point d’arrêt et les lignes d’exécution actuelles sont automatiquement mis en évidence. Pour le code CMD, vous pouvez activer la mise en évidence du point d’arrêt et des lignes actuelles en sélectionnant **des outils** (ou **Debug**) > **Options** > **Debugging** >  **Highlight ligne source entière pour les points de rupture et l’instruction actuelle (C seulement)**.

![Définir un point d’arrêt](../debugger/media/basicbreakpoint.png "Point d’arrêt de base")

Lorsque vous déboignez, l’exécution s’arrête au point d’arrêt, avant que le code sur cette ligne soit exécuté. Le symbole de point d’arrêt montre une flèche jaune.

Au point d’arrêt dans l’exemple suivant, la valeur de `testInt` est encore de 1. Ainsi, la valeur n’a pas changé depuis que la variable a été paraspéisée (réglée à une valeur de 1) parce que la déclaration en jaune n’a pas encore exécuté.

![L'exécution du point d'arrêt s'est arrêtée](../debugger/media/breakpointexecution.png "Exécution de point de rupture")

Lorsque le débbuggeur s’arrête au point d’arrêt, vous pouvez regarder l’état actuel de l’application, y compris les [valeurs variables](../debugger/debugger-feature-tour.md#inspect-variables-with-data-tips) et la [pile d’appels](../debugger/how-to-use-the-call-stack-window.md).

Voici quelques instructions générales pour travailler avec des points d’arrêt.

- Le point d’arrêt est un basculement. Vous pouvez cliquer dessus, appuyer sur **F9**ou utiliser **Debug** > **Toggle Breakpoint** pour le supprimer ou le réinsérer.

- Pour désactiver un point d’arrêt sans le supprimer, planer ou cliquer à droite, et sélectionner **le point d’arrêt Désactiver**. Les points d’arrêt désactivés apparaissent comme des points vides dans la marge gauche ou la fenêtre **Breakpoints.** Pour ré-activer un point d’arrêt, planer au-dessus ou à droite, et **sélectionnez Activez le point d’arrêt**.

- Définissez les conditions et les actions, ajoutez et modifiez les étiquettes, ou exportez un point d’arrêt en le cliquant à droite et en sélectionnant la commande appropriée, ou en planant au-dessus de celui-ci et en sélectionnant **l’icône Paramètres.**

## <a name="breakpoint-actions-and-tracepoints"></a><a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a>Actions et points de traçabilité

Un *point de trace* est un point d’arrêt qui imprime un message à la fenêtre de **sortie.** Un tracepoint peut agir comme une trace temporaire dans le langage de programmation et ne met pas en pause l’exécution du code. Vous créez un point de traçabilité en définissant une action spéciale dans la fenêtre **Paramètres De point de rupture.** Pour des instructions détaillées, voir [Utilisez des tracepoints dans le debugger Visual Studio](../debugger/using-tracepoints.md).

## <a name="breakpoint-conditions"></a>Conditions de point d’arrêt

Vous pouvez contrôler quand et où un point d’arrêt s’exécute en définissant des conditions. La condition peut être n’importe quelle expression valide que le débbuggeur reconnaît. Pour plus d’informations sur les expressions valides, consultez [Expressions dans le débogueur](../debugger/expressions-in-the-debugger.md).

**Pour définir une condition de point d’arrêt :**

1. Cliquez à droite sur le symbole du point d’arrêt et sélectionnez **conditions**. Ou planez au-dessus du symbole de point d’arrêt, sélectionnez **l’icône Paramètres,** puis sélectionnez **les conditions** dans la fenêtre Paramètres de point **de rupture.**

   Vous pouvez également définir des conditions dans la fenêtre **Breakpoints** en cliquant à droite sur un point d’arrêt et en sélectionnant **paramètres,** puis en sélectionnant les **conditions**.

   ![Paramètres de point d’arrêt](../debugger/media/breakpointsettings.png "BreakpointSettings")

2. Dans le dropdown, sélectionnez **l’expression conditionnelle**, **Hit Count**, ou **Filtre**, et définissez la valeur en conséquence.

3. Sélectionnez **Fermer** ou appuyez sur **Ctrl**+**Enter** pour fermer la fenêtre Paramètres De **point de** rupture. Ou, à partir de la fenêtre **Breakpoints,** sélectionnez **OK** pour fermer le dialogue.

Les points de rupture avec **+** les conditions définies apparaissent avec un symbole dans le code source et les fenêtres **Breakpoints.**

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="create-a-conditional-expression"></a>Créer une expression conditionnelle

Lorsque vous sélectionnez **l’expression conditionnelle**, vous pouvez choisir entre deux conditions: **Est vrai** ou **Lorsqu’il est changé**. Choisir **est vrai** de se briser lorsque l’expression est satisfaite, ou Quand **changé** pour casser lorsque la valeur de l’expression a changé.

Dans l’exemple suivant, le point d’arrêt n’est atteint que lorsque la valeur est de `testInt` **4**:

![La condition de point d'arrêt a la valeur true](../debugger/media/breakpointconditionistrue.png "Breakpoint est vrai")

Dans l’exemple suivant, le point d’arrêt n’est atteint que lorsque la valeur des `testInt` modifications :

![Point d’arrêt Lorsqu’il est modifié](../debugger/media/breakpointwhenchanged.png "Point d’arrêt Lorsqu’il est modifié")

Si vous définissez une condition de point d’arrêt dont la syntaxe est incorrecte, un message d’avertissement s’affiche. Si vous spécifiez une condition de point d’arrêt avec une syntaxe valide, mais dont la sémantique n’est pas valide, un message d’avertissement apparaît quand le point d’arrêt est atteint pour la première fois. Dans les deux cas, le débbuggeur se casse lorsqu’il atteint le point d’arrêt invalide. Le point d’arrêt n’est ignoré que si la condition est valide et prend la valeur `false`.

>[!NOTE]
>Le comportement du champ **Quand changé** est différent pour les différents langages de programmation.
>- Pour le code natif, le débbuggeur ne considère pas la première évaluation de la condition comme un changement, donc ne touche pas le point d’arrêt sur la première évaluation.
>- Pour le code géré, le débbuggeur frappe le point d’arrêt de la première évaluation après **la sélection de When changed.**

<a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>
### <a name="use-object-ids-in-conditional-expressions-c-and-f-only"></a>Utilisez des ID d’objets dans des expressions conditionnelles (C et F seulement)

 Il ya des moments où vous voulez observer le comportement d’un objet spécifique. Par exemple, vous pouvez savoir pourquoi un objet a été inséré dans une collection plus d’une fois. En C# et en F#, vous pouvez créer des ID d’objet pour des instances spécifiques de [types référence](/dotnet/csharp/language-reference/keywords/reference-types) et les utiliser dans des conditions de point d’arrêt. L’ID d’objet est généré par les services de débogage du Common Language Runtime (CLR) et associé à l’objet.

**Pour créer un identifiant d’objet :**

1. Définissez un point d’arrêt dans le code quelque place après la création de l’objet.

2. Commencez à déboguer, et lorsque l’exécution s’arrête au point d’arrêt, sélectionnez **Debug** > **Windows** > **Locals** ou **Alt**+**4** pour ouvrir la fenêtre **local.**

   Trouvez l’instance d’objet spécifique dans la fenêtre **Locals,** cliquez dessus à droite et **sélectionnez Make Object ID**.

   Vous devriez **$** voir un plus un numéro dans la fenêtre **des sections locales.** Il s’agit de l’ID d’objet.

3. Ajoutez un nouveau point d’arrêt au point que vous souhaitez étudier; par exemple, lorsque l’objet doit être ajouté à la collection. Cliquez avec le bouton droit sur le point d’arrêt et sélectionnez **Conditions**.

4. Utilisez l’ID d’objet dans le champ **Expression conditionnelle.** Par exemple, si `item` la variable est l’objet à ajouter à la collection, sélectionnez \<Est **vrai** et type élément **n\<>**, où n> est le numéro d’identification de l’objet.

   L’exécution s’arrête au point où cet objet doit être ajouté à la collection.

   Pour supprimer l’identifiant d’objet, cliquez à droite sur la variable dans la fenêtre **Locals** et **sélectionnez Supprimer l’identifiant d’objet**.

> [!NOTE]
> Les ID d’objet créent des références faibles et n’empêchent pas l’objet de subir une récupération de mémoire. Leur validité ne vaut que pour la session de débogage active.

### <a name="set-a-hit-count-condition"></a>Définir une condition de nombre de coups

Si vous soupçonnez qu’une boucle dans votre code commence à se comporter mal après un certain nombre d’itérations, vous pouvez définir un point d’arrêt pour arrêter l’exécution après ce nombre de coups, plutôt que d’avoir à appuyer à plusieurs reprises **sur F5** pour atteindre cette itération.

Dans **les conditions** dans la fenêtre Paramètres de point **d’arrêt,** sélectionnez **Hit Count,** puis spécifiez le nombre d’itérations. Dans l’exemple suivant, le point d’arrêt est configuré pour frapper sur toutes les autres itérations:

![Nombre de coups de point de rupture](../debugger/media/breakpointhitcount.png "BreakpointHitCount")

### <a name="set-a-filter-condition"></a>Définir une condition de filtre

Vous pouvez limiter le déclenchement d’un point d’arrêt seulement sur des appareils spécifiés ou dans des processus et des threads spécifiés.

Dans **les conditions** dans la fenêtre Paramètres de point **d’arrêt,** sélectionnez **filtre,** puis entrez une ou plusieurs des expressions suivantes :

- MachineName = "nom"
- ProcessId = valeur
- ProcessName = "nom"
- ThreadId = valeur
- ThreadName = "nom"

Placez les valeurs de chaîne entre guillemets doubles. Vous pouvez combiner des clauses à l’aide de `&` (AND), `||` (OR), `!` (NOT) et de parenthèses.

## <a name="set-function-breakpoints"></a><a name="BKMK_Set_a_breakpoint_in_a_source_file"></a>Définir les points d’arrêt de la fonction

Vous pouvez briser l’exécution lorsqu’une fonction est appelée. Ceci est utile, par exemple, lorsque vous connaissez le nom de la fonction, mais pas son emplacement. Il est également utile si vous avez des fonctions avec le même nom et que vous voulez briser sur tous (tels que les fonctions surchargées ou des fonctions dans différents projets).

**Pour définir un point d’arrêt de la fonction :**

1. Sélectionnez **Debug** > **New Breakpoint** > **Function Breakpoint**, ou appuyez sur **Alt**+**F9** > **Ctrl**+**B**.

   Vous pouvez également sélectionner **New** > **Function Breakpoint** dans la fenêtre **Breakpoints.**

1. Dans le **dialogue New Function Breakpoint,** entrez le nom de fonction dans la boîte **nom de fonction.**

   Pour réduire la spécification de la fonction :

   - Utilisez le nom de fonction entièrement qualifié.

     Exemple : `Namespace1.ClassX.MethodA()`

   - Ajouter les types de paramètres d’une fonction surchargée.

     Exemple : `MethodA(int, string)`

   - Utilisez le symbole '!' pour spécifier le module.

     Exemple : `App1.dll!MethodA`

   - Utilisez l’opérateur de contexte dans le C.C. natif.

     `{function, , [module]} [+<line offset from start of method>]`

     Exemple : `{MethodA, , App1.dll}+2`

1. Dans le **décrocheur de la langue,** choisissez la langue de la fonction.

1. Sélectionnez **OK**.

### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Définissez un point d’arrêt de fonction à l’aide d’une adresse mémoire (native CMD seulement)
 Vous pouvez utiliser l’adresse d’un objet pour définir un point d’arrêt de fonction sur une méthode appelée par un exemple spécifique d’une classe.  Par exemple, compte tenu d’un objet de type `my_class`adressable, vous pouvez définir un point d’arrêt de fonction sur la `my_method` méthode que l’instance appelle.

1. Définissez un point d’arrêt quelque part après l’arrivée instantanée de l’instance de la classe.

2. Trouvez l’adresse de l’instance (par exemple, `0xcccccccc`).

3. Sélectionnez **Debug** > **New Breakpoint** > **Function Breakpoint**, ou appuyez sur **Alt**+**F9** > **Ctrl**+**B**.

4. Ajoutez ce qui suit à la boîte **de nom de fonction** et sélectionnez la langue de **CMD.**

   ```cpp
   ((my_class *) 0xcccccccc)->my_method
   ```

::: moniker range=">= vs-2019"

## <a name="set-data-breakpoints-net-core-30-or-higher"></a><a name="BKMK_set_a_data_breakpoint_managed"></a>Définir les points d’arrêt des données (.NET Core 3.0 ou plus)

Les points d’arrêt de données cassent l’exécution lorsque la propriété d’un objet spécifique change.

**Définir un point d’arrêt de données**

1. Dans un projet .NET Core, commencez à débogage et attendez qu’un point d’arrêt soit atteint.

2. Dans la fenêtre **Autos**, **Watch**, ou **Locals,** cliquez à droite sur une propriété et **sélectionnez Pause lorsque** la valeur change dans le menu contexte.

    ![Point d’arrêt de données gérés](../debugger/media/managed-data-breakpoint.png "Point d’arrêt de données gérés")

Les points d’arrêt de données dans .NET Core ne fonctionneront pas pour :

- Propriétés qui ne sont pas extensibles dans la pointe d’outils, les sections locales, les automobiles ou la fenêtre de montre
- Variables statiques
- Classes avec l’attribut DebuggerTypeProxy
- Champs à l’intérieur des structs

::: moniker-end

## <a name="set-data-breakpoints-native-c-only"></a><a name="BKMK_set_a_data_breakpoint_native_cplusplus"></a>Définir des points d’arrêt de données (natif Cmd seulement)

 Les points d’arrêt de données cassent l’exécution lorsqu’une valeur stockée à une adresse mémoire spécifiée change. Si la valeur est lue mais pas modifiée, l’exécution ne s’interrompt pas.

**Pour définir un point d’arrêt de données :**

1. Dans le cadre d’un projet de CMD, commencez à débogage et attendez qu’un point d’arrêt soit atteint. Sur le menu **Debug,** choisissez **New Breakpoint** > **Data Breakpoint**

    Vous pouvez également sélectionner **le nouveau** > **point d’arrêt de données** dans la fenêtre **Breakpoints** ou cliquer à droite sur un élément de la fenêtre **Autos,** **Watch**, ou **Locals** et sélectionner **Break lorsque** la valeur change dans le menu context.

2. Dans la boîte **d’adresse,** tapez une adresse mémoire ou une expression qui s’évalue à une adresse mémoire. Par exemple, tapez `&avar` pour interrompre l’exécution quand le contenu de la variable `avar` change.

3. Dans la zone déroulante **Nombre d’octets** , sélectionnez le nombre d’octets que le débogueur doit surveiller. Par exemple, si vous sélectionnez **4**, le débogueur surveille les quatre octets à partir de `&avar` et interrompt l’exécution si l’un de ces octets change de valeur.

Les points d’arrêt de données ne fonctionnent pas dans les conditions suivantes :
- Un processus qui n’est pas en cours de débogage écrit à l’emplacement mémoire.
- L’emplacement mémoire est partagé entre plusieurs processus.
- L’emplacement de mémoire est mis à jour dans le noyau. Par exemple, si la mémoire est transmise `ReadFile` à la fonction Windows 32 bits, la mémoire sera mise à jour à partir du mode noyau, de sorte que le débbuggeur ne se casse pas sur la mise à jour.
- Lorsque l’expression de la montre est plus grande que 4 octets sur le matériel 32 bits et 8 octets sur le matériel 64 bits. Il s’agit d’une limitation de l’architecture x86.

> [!NOTE]
> - Les points d’arrêt de données dépendent d’adresses mémoire spécifiques. L’adresse d’une variable passe d’une session de débogage à l’autre, de sorte que les points d’arrêt des données sont automatiquement désactivés à la fin de chaque session de débogage.
>
> - Si vous définissez un point d’arrêt sur une variable locale, ce point d’arrêt reste activé quand la fonction s’arrête. Cependant, l’adresse mémoire n’est plus applicable, et le comportement du point d’arrêt est donc imprévisible. Si vous définissez un point d’arrêt de données sur une variable locale, vous devez supprimer ou désactiver le point d’arrêt avant la fin de la fonction.

## <a name="manage-breakpoints-in-the-breakpoints-window"></a><a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Gérer les points d’arrêt dans la fenêtre Points d’arrêt

 Vous pouvez utiliser la fenêtre **Breakpoints** pour voir et gérer tous les points d’arrêt de votre solution. Cet emplacement centralisé est particulièrement utile dans une grande solution, ou pour les scénarios complexes de débogage où les points d’arrêt sont critiques.

Dans la fenêtre **Breakpoints,** vous pouvez rechercher, trier, filtrer, activer/désactiver ou supprimer les points d’arrêt. Vous pouvez également définir des conditions et des actions, ou ajouter une nouvelle fonction ou un nouveau point d’arrêt de données.

Pour ouvrir la fenêtre **Breakpoints,** sélectionnez **Debug** > **Windows** > **Breakpoints**, ou appuyez sur **Alt**+**F9** ou **Ctrl**+**Alt**+**B**.

![Fenêtre de breakpoints](../debugger/media/breakpointswindow.png "Points d'arrêt (fenêtre)")

Pour sélectionner les colonnes à afficher dans la fenêtre **Breakpoints,** sélectionnez **Afficher les colonnes**. Sélectionnez un en-tête de colonne pour trier la liste des points d’arrêt par cette colonne.

### <a name="breakpoint-labels"></a><a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Étiquettes de point d’arrêt
Vous pouvez utiliser des étiquettes pour trier et filtrer la liste des points d’arrêt dans la fenêtre **Breakpoints.**

1. Pour ajouter une étiquette à un point d’arrêt, cliquez à droite sur le point d’arrêt du code source ou de la fenêtre **Breakpoints,** puis sélectionnez **les étiquettes Edit**. Ajouter une nouvelle étiquette ou choisir une étiquette existante, puis sélectionnez **OK**.
2. Trier la liste de point d’arrêt dans la fenêtre **Breakpoints** en sélectionnant les **étiquettes,** **conditions,** ou d’autres en-têtes de colonne. Vous pouvez sélectionner les colonnes à afficher en sélectionnant les **colonnes d’affichage** dans la barre d’outils.

### <a name="export-and-import-breakpoints"></a>Exporter et importer les points d'arrêt
 Pour économiser ou partager l’état et l’emplacement de vos points d’arrêt, vous pouvez les exporter ou les importer.

- Pour exporter un point d’arrêt unique vers un fichier XML, cliquez à droite sur le point d’arrêt du code source ou de la fenêtre **Breakpoints,** et sélectionnez **Export** ou **Export sélectionnés**. Sélectionnez un emplacement d’exportation, puis sélectionnez **Enregistrer**. L’emplacement par défaut est le dossier de solution.
- Pour exporter plusieurs points d’arrêt, dans la fenêtre **Breakpoints,** sélectionnez les cases à côté des points d’arrêt, ou entrez les critères de recherche dans le champ **de recherche.** Sélectionnez **l’exportation tous les points d’arrêt correspondant à l’icône actuelle des critères de recherche** et enregistrez le fichier.
- Pour exporter tous les points d’arrêt, désélectionner toutes les cases et laisser le champ **de recherche** vide. Sélectionnez **l’exportation tous les points d’arrêt correspondant à l’icône actuelle des critères de recherche** et enregistrez le fichier.
- Pour importer des points d’arrêt, dans la fenêtre **Breakpoints,** sélectionnez les **points d’arrêt Import à partir d’une** icône de fichier, naviguez vers l’emplacement du fichier XML et sélectionnez **Open**.

## <a name="set-breakpoints-from-debugger-windows"></a><a name="BKMK_Set_a_breakpoint_from_debugger_windows"></a>Définir les points d’arrêt des fenêtres de débbugger

Vous pouvez également définir les points d’arrêt à partir de la **pile d’appels** et **démonter** les fenêtres démontage.

### <a name="set-a-breakpoint-in-the-call-stack-window"></a>Définissez un point d’arrêt dans la fenêtre Call Stack

 Pour vous casser à l’instruction ou à la ligne à laquelle une fonction d’appel retourne, vous pouvez définir un point d’arrêt dans la fenêtre **Call Stack.**

**Pour définir un point d’arrêt dans la fenêtre Call Stack :**

1. Pour ouvrir la fenêtre **Call Stack,** vous devez être mis en pause pendant le débogage. Sélectionnez **Debug** > **Windows** > **Call Stack**, ou appuyez sur **Ctrl**+**Alt**+**C**.

2. Dans la fenêtre **Call Stack,** cliquez à droite sur la fonction d’appel et **sélectionnez Breakpoint** > **Insert Breakpoint**, ou appuyez sur **F9**.

   Un symbole de point d’arrêt apparaît à côté du nom d’appel de fonction dans la marge gauche de la pile d’appel.

Le point de rupture de pile d’appel apparaît dans la fenêtre **Breakpoints** comme une adresse, avec un emplacement de mémoire qui correspond à la prochaine instruction exécutable dans la fonction.

Le débagé se casse à l’instruction.

Pour plus d’informations sur la pile des appels, consultez [Comment : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md).

Pour tracer visuellement les points d’arrêt pendant l’exécution du code, voir [les méthodes de carte sur la pile d’appel tout en débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Définissez un point d’arrêt dans la fenêtre de démontage

1. Pour ouvrir la fenêtre **de démontage,** vous devez être mis en pause pendant le débogage. Sélectionnez **Debug** > **Windows** > **Disassembly**, ou appuyez sur **Alt**+**8**.

2. Dans la fenêtre **démontage,** cliquez sur la marge gauche de l’instruction à laquelle vous voulez vous briser. Vous pouvez également le sélectionner et appuyez sur **F9**, ou clic droit et **sélectionnez Breakpoint** > **Insert Breakpoint**.

## <a name="see-also"></a>Voir aussi

- [Qu’est-ce que le débogage ?](../debugger/what-is-debugging.md)
- [Écrivez un meilleur code C à l’aide de Visual Studio](../debugger/write-better-code-with-visual-studio.md)
- [Premier regard sur le débogage](../debugger/debugger-feature-tour.md)
- [Points d’arrêt de dépannage dans le debugger Visual Studio](../debugger/troubleshooting-breakpoints.md)
