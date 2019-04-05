---
title: À l’aide de points d’arrêt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpointswin
- vs.debug.disassembly.insert
- vs.debug.sourcewin.edit
- vs.debug.file
- vs.debug.breakpt.new
- vs.debug.whenbreakpointishit
- vs.debug.breakpt.choose
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
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
caps.latest.revision: 63
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ff5858482f64e8e73844c433febe8033b7ab1d70
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58947910"
---
# <a name="using-breakpoints"></a>Utilisation des points d'arrêt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Vous pouvez définir des points d’arrêt quand vous voulez interrompre l’exécution du débogueur, éventuellement pour voir l’état des variables de code ou examiner la pile des appels. Ils constituent l’une des techniques de débogage les plus importantes de la boîte à outils d’un développeur.
  
##  <a name="BKMK_Overview"></a> Définition d’un point d’arrêt sur fonction dans le code source  
 Vous pouvez définir un point d’arrêt sur fonction dans le code source en cliquant dans la marge de gauche d’un fichier de code source ou en plaçant votre curseur sur une ligne de code et en appuyant sur F9. Le point d’arrêt apparaît sous forme de point rouge dans la marge de gauche, et la ligne de code est aussi en couleur :  
  
 ![Définissez un point d’arrêt](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Quand vous exécutez ce code dans le débogueur, l’exécution s’interrompt chaque fois que le point d’arrêt est atteint, avant que le code de cette ligne soit exécuté. La ligne de code source est de couleur jaune :  
  
 ![L’exécution de point d’arrêt s’est arrêtée](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 À ce stade, la valeur de `testInt` est toujours égale à 1.  
  
 Vous pouvez examiner l’état actuel de l’application, y compris les valeurs de variables et la pile des appels. Pour plus d’informations sur la pile des appels, consultez [Comment : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md).  
  
 Vous pouvez définir un point d’arrêt sur n’importe quelle ligne de code exécutable. Par exemple, dans le code C# ci-dessus, vous pouvez définir un point d’arrêt sur la déclaration des variables, la boucle `for` ou tout code à l’intérieur de la boucle `for` , mais vous ne pouvez pas définir un point d’arrêt sur les déclarations d’espace de noms ou de classe ou la signature de la méthode.  
  
##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Définition d’autres types de points d’arrêt  
 Vous pouvez aussi définir des points d’arrêt dans la pile des appels, dans la fenêtre Code machine et, dans le code C++ natif, au niveau d’une condition de données ou d’une adresse mémoire.  
  
## <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> Définition d’un point d’arrêt dans la fenêtre Pile des appels  
 Vous pouvez arrêter l’exécution au niveau de l’instruction ou de la ligne à laquelle une fonction appelante retourne une valeur en définissant un point d’arrêt dans la fenêtre **Pile des appels** . Pour plus d’informations sur la pile des appels, consultez [Comment : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md). Le débogueur doit avoir interrompu l’exécution.  
  
1. Commencez le débogage de l’application, puis attendez que l’exécution soit interrompue (par exemple, au niveau d’un point d’arrêt). Ouvrez la fenêtre **Pile des appels** (**Déboguer/Fenêtres/Pile des appels**ou **Ctrl+Alt+C**).  
  
2. Cliquez avec le bouton droit sur la fonction d’appel, puis sélectionnez **Point d’arrêt/Insérer un point d’arrêt**ou utilisez simplement la touche de raccourci **F9**.  
  
3. Un symbole de point d’arrêt apparaît dans la marge de gauche de la pile des appels, en regard du nom de l’appel de fonction.  
  
   Dans la fenêtre **Points d’arrêt** , le point d’arrêt de pile des appels apparaît sous la forme d’une adresse avec un emplacement de mémoire correspondant à la prochaine instruction exécutable de la fonction. Le débogueur arrête l’exécution au niveau de l’instruction.  
  
   À visuellement trace des points d’arrêt pendant l’exécution de code, consultez [mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## <a name="setting-a-breakpoint-in-the-disassembly-window"></a>Définition d’un point d’arrêt dans la fenêtre Code machine  
 Pour définir un point d’arrêt au niveau d’une instruction assembly, le débogueur doit être en mode arrêt.  
  
1.  Commencez le débogage de l’application, puis attendez que l’exécution soit interrompue (par exemple, au niveau d’un point d’arrêt). Ouvrez la fenêtre **Code Machine** (**Déboguer/Fenêtres/Code Machine**ou **Ctrl+Alt+D**).  
  
2.  Cliquez dans la marge de gauche au niveau de l’instruction où vous voulez effectuer l’arrêt ou définissez votre curseur au niveau de l’instruction et appuyez sur **F9**.  
  
## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a> Définir un point d’arrêt de données (natif C++ uniquement)  
 Les points d’arrêt sur variable interrompent l’exécution quand une valeur stockée à l’adresse mémoire spécifiée change. Si la valeur est lue mais pas modifiée, l’exécution ne s’interrompt pas. Pour définir des points d’arrêt sur variable, le débogueur doit être en mode arrêt.  
  
1. Commencez le débogage de l’application et attendez qu’un point d’arrêt soit atteint. Dans le menu **Déboguer** , choisissez **Nouveau point d’arrêt/Point d’arrêt sur variable** (ou ouvrez la fenêtre **Points d’arrêt** et choisissez **Nouveau/Point d’arrêt sur variable**.  
  
2. Dans la zone **Adresse** , tapez une adresse mémoire ou une expression qui prend comme valeur une adresse mémoire. Par exemple, tapez `&avar` pour interrompre l’exécution quand le contenu de la variable `avar` change.  
  
3. Dans la zone déroulante **Nombre d’octets** , sélectionnez le nombre d’octets que le débogueur doit surveiller. Par exemple, si vous sélectionnez **4**, le débogueur surveille les quatre octets à partir de `&avar` et interrompt l’exécution si l’un de ces octets change de valeur.  
  
   N’oubliez pas que les points d’arrêt sur variable dépendent de l’applicabilité d’adresses mémoire spécifiques.  
  
- L’adresse d’une variable change d’une session de débogage à la suivante. Les points d’arrêt sur variable sont automatiquement désactivés à la fin de chaque session de débogage.  
  
- Si vous définissez un point d’arrêt sur une variable locale, ce point d’arrêt reste activé quand la fonction s’arrête. Cependant, l’adresse mémoire n’est plus applicable et le comportement du point d’arrêt est imprévisible. Si vous définissez un point d’arrêt sur une variable locale, vous devez le supprimer ou le désactiver avant la fin de la fonction.  
  
  Les points d’arrêt sur variable ne fonctionnent pas dans les conditions suivantes :  
  
- Un processus qui n’est pas en cours de débogage écrit dans l’emplacement de mémoire.  
  
- L’emplacement de mémoire est partagé entre plusieurs processus.  
  
- L’emplacement de mémoire est mis à jour dans le noyau. Par exemple, si la mémoire est passée à la fonction `ReadFile` Windows 32 bits, elle est mise à jour à partir du mode noyau et le débogueur ne s’interrompt pas en cas d’écriture en mémoire.  
  
## <a name="setting-a-breakpoint-with-a-memory-address-native-c-only"></a>Définition d’un point d’arrêt avec une adresse mémoire (C++ natif uniquement)  
 Vous pouvez aussi utiliser l’adresse d’un objet pour définir un point d’arrêt sur une méthode appelée sur une instance spécifique d’une classe.  Voici un exemple :  
  
 Si vous partez d’un objet de type `my_class` avec l’adresse, vous pouvez définir un point d’arrêt sur fonction sur une méthode nommée `my_method` appelée à partir de cette instance.  
  
1.  Définissez un point d’arrêt quelque part après que l’instance de la classe est instanciée.  
  
2.  Recherchez l’adresse de l’instance ( `0xcccccccc`dans cet exemple).  
  
3.  Cliquez sur **Déboguer/Nouveau point d’arrêt/Point d’arrêt sur fonction** (ou **Alt+F9, B**).  
  
4.  Ajoutez le texte suivant dans la zone **Nom de la fonction** :  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Gestion des points d’arrêt  
 Vous pouvez utiliser la fenêtre **Points d’arrêt** (**Déboguer/Fenêtres/Points d’arrêt**ou **Ctrl+Alt+B**) pour afficher tous les points d’arrêt que vous avez définis dans votre solution :  
  
 ![Fenêtre points d’arrêt](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 La fenêtre **Points d’arrêt** est un emplacement centralisé d’où vous pouvez gérer tous vos points d’arrêt, ce qui peut être particulièrement utile dans une solution de grande taille ou dans un scénario de débogage complexe où les points d’arrêt sont déterminants. Si vous devez enregistrer ou partager l’état et l’emplacement d’un ensemble de points d’arrêt, vous pouvez exporter et importer des points d’arrêt uniquement à partir de la fenêtre **Points d’arrêt** .  
  
##  <a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a> Points d’arrêt avancés  
  
## <a name="breakpoint-conditions"></a>Conditions de point d’arrêt  
 Vous pouvez contrôler quand et où un point d’arrêt s’exécute en définissant des conditions.  
  
1. Cliquez avec le bouton droit sur le point d’arrêt ou pointez dessus et choisissez l’icône des paramètres.  
  
2. Dans le menu contextuel, sélectionnez **Conditions**. La fenêtre **Paramètres de point d’arrêt** s’ouvre :  
  
   ![Paramètres de point d’arrêt](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
   Quand vous cochez la case **Conditions** , la fenêtre se développe pour afficher les différents types de conditions.  
  
   **Expression conditionnelle :** Lorsque vous sélectionnez Expression conditionnelle, vous pouvez ensuite choisir deux conditions : **A la valeur true** et **lorsque modifié**. Choisissez **Est true** pour arrêter l’exécution quand l’expression est satisfaite ou **En cas de modification** pour l’arrêter quand la valeur de l’expression a changé.  
  
   Dans l’exemple suivant, nous avons défini que le point d’arrêt est atteint uniquement quand la valeur de `testInt` est égale à **4**:  
  
   ![Condition de point d’arrêt est true](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
   Dans l’exemple suivant, nous avons défini que le point d’arrêt est atteint uniquement quand la valeur de `testInt` change :  
  
   ![Point d’arrêt lorsque modifié](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
   Le comportement du champ En cas de modification varie en fonction du langage de programmation. Si vous choisissez **En cas de modification** pour du code natif, le débogueur ne considère pas la première évaluation de la condition comme étant une modification : le point d’arrêt n’est donc pas atteint à la première évaluation. Si vous sélectionnez **En cas de modification** pour du code managé, le point d’arrêt est atteint à la première évaluation après que **En cas de modification** a été sélectionné.  
  
   Si vous définissez une condition de point d’arrêt dont la syntaxe est incorrecte, un message d’avertissement s’affiche. Si vous spécifiez une condition de point d’arrêt avec une syntaxe valide, mais dont la sémantique n’est pas valide, un message d’avertissement apparaît quand le point d’arrêt est atteint pour la première fois. Dans les deux cas, le débogueur arrête l’exécution quand le point d’arrêt non valide est atteint. Le point d’arrêt n’est ignoré que si la condition est valide et prend la valeur `false`.  
  
   La condition peut être n’importe quelle expression valide reconnue par le débogueur. Pour plus d’informations sur les expressions valides, consultez [Expressions in the Debugger](../debugger/expressions-in-the-debugger.md).  
  
## <a name="using-object-ids-in-breakpoint-conditions-c-and-f"></a>Utilisation d’ID d’objet dans des conditions de point d’arrêt (C# et F#)  
 Vous voulez parfois observer le comportement d’un objet spécifique ; par exemple, vous pouvez vouloir découvrir pourquoi un objet a été inséré plusieurs fois dans une collection. En C# et en F#, vous pouvez créer des ID d’objet pour des instances spécifiques de [types référence](http://msdn.microsoft.com/library/801cf030-6e2d-4a0d-9daf-1431b0c31f47) et les utiliser dans des conditions de point d’arrêt. L’ID d’objet est généré par les services de débogage du Common Language Runtime (CLR) et associé à l’objet.  Pour créer un ID d’objet, procédez comme suit :  
  
1. Définissez un point d’arrêt dans le code quelque temps après que l’objet a été créé.  
  
2. Démarrez le débogage, puis, quand l’exécution s’interrompt au point d’arrêt, recherchez le point d’arrêt dans la fenêtre **Variables locales** , cliquez dessus avec le bouton droit, puis sélectionnez **Générer ID de l’objet**.  
  
    Le symbole **$** et un nombre s’affichent alors dans la fenêtre **Variables locales** . Il s’agit de l’ID d’objet.  
  
3. Ajoutez un nouveau point d’arrêt conditionnel au point vous voulez étudier, par exemple l’endroit où l’objet doit être ajouté à la collection.  
  
4. Utilisez l’ID d’objet dans le champ Expression conditionnelle. Par exemple, si une variable `item` faisant référence à l’objet doit être ajoutée à la collection, vous devez placer **item == $n**, où **n** est le numéro d’ID d’objet.  
  
    L’exécution s’arrête au point où cet objet doit être ajouté à la collection.  
  
   Si vous voulez supprimer ultérieurement l’ID d’objet, vous pouvez cliquer avec le bouton droit sur la variable dans la fenêtre **Variables locales** , puis sélectionnez **Supprimer l’ID de l’objet**.  
  
   Notez que les ID d’objet créent des références faibles et n’empêchent pas l’objet d’être récupéré par le garbage collector. Leur validité ne vaut que pour la session de débogage active.  
  
## <a name="hit-count"></a>Nombre d’accès  
 Si vous pensez qu’une boucle de votre code commence à avoir un comportement anormal après un certain nombre d’itérations, vous pouvez définir un point d’arrêt pour interrompre l’exécution au bout d’un nombre d’accès spécifié sur la ligne de code associée, au lieu de devoir appuyer plusieurs fois sur **F5** pour atteindre le niveau d’itération.  
  
 Dans la fenêtre **Paramètres de point d’arrêt** , définissez **Nombre d’accès**comme condition. Vous pouvez dès lors spécifier le nombre d’itérations. Dans l’exemple suivant, nous avons défini que le point d’arrêt est atteint à chaque autre itération :  
  
 ![Nombre d’accès de point d’arrêt](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## <a name="filter"></a>Filtre  
 Vous pouvez limiter le déclenchement d’un point d’arrêt seulement sur des appareils spécifiés ou dans des processus et des threads spécifiés.  
  
 Dans la fenêtre **Paramètres de point d’arrêt**, définissez **Filtre**comme condition. Entrez une ou plusieurs des expressions suivantes :  
  
- MachineName = "nom"  
  
- ProcessId = valeur  
  
- ProcessName = "nom"  
  
- ThreadId = valeur  
  
- ThreadName = "nom"  
  
  Placez les valeurs de chaîne entre guillemets doubles. Vous pouvez combiner des clauses à l’aide de `&` (AND), `||` (OR), `!` (NOT) et de parenthèses.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Actions de points d’arrêt et points de trace  
 Un point de trace est un point d’arrêt qui affiche un message dans la fenêtre Sortie. Un point de trace peut faire office d’instruction de trace temporaire dans le langage de programmation.  
  
 Dans la fenêtre **Paramètres de point d’arrêt** , cochez la case **Actions** . Choisissez **Enregistrer les messages dans la fenêtre Sortie** dans le groupe **Action** . Vous pouvez imprimer une chaîne générique, telle que **ceci est un test**. Pour inclure la valeur d’une variable ou d’une expression, vous devez la placer entre accolades.  
  
 Pour arrêter l’exécution quand le point de trace est atteint, décochez la case **Continuer l’exécution** . Quand **Continuer l’exécution** est coché, l’exécution n’est pas interrompue. Dans les deux cas, le message est imprimé.  
  
 Vous pouvez utiliser les mots clés spéciaux suivants dans le **Message**.  
  
|||  
|-|-|  
|**$ADDRESS**|Instruction actuelle|  
|**$CALLER**|Nom de la fonction appelante|  
|**$CALLSTACK**|Pile des appels|  
|**$FUNCTION**|Nom de la fonction actuelle|  
|**$PID**|ID du processus|  
|**$PNAME**|Nom du processus|  
|**$TID**|ID du thread|  
|**$TNAME**|Nom du thread|  
|**$TICK**||  
|**$TNAME**||  
  
##  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Étiquettes de point d’arrêt  
 Les étiquettes de point d’arrêt sont utilisées uniquement dans la fenêtre **Points d’arrêt** pour trier et filtrer la liste des points d’arrêt. Pour ajouter une étiquette à un point d’arrêt, choisissez la ligne de point d’arrêt, puis choisissez **Étiquette** dans le menu contextuel.  
  
## <a name="export-and-import-breakpoints"></a>Exporter et importer des points d’arrêt  
 Vous pouvez exporter un point d’arrêt vers un fichier XML en cliquant avec le bouton droit sur le point d’arrêt et en sélectionnant **Exporter**. Le fichier est enregistré par défaut dans le répertoire de la solution. Pour importer des points d’arrêt, ouvrez la fenêtre **Points d’arrêt** (**Ctrl+Alt+B**) puis, dans la barre d’outils, cliquez sur la flèche pointant vers la droite (l’info-bulle est **Importer les points d’arrêt d’un fichier**).  
  
## <a name="troubleshoot-breakpoints"></a>Résoudre les problèmes liés aux points d’arrêt  
  
### <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>J’ai supprimé un point d’arrêt, mais je continue de l’atteindre quand je relance le débogage  
 Si vous avez supprimé un point d’arrêt pendant le débogage, il est possible dans certains cas que vous atteigniez à nouveau le point d’arrêt au prochain lancement du débogage. Pour cesser d’atteindre ce point d’arrêt, assurez-vous que toutes les instances du point d’arrêt sont supprimées de la fenêtre **Points d’arrêt** .  
  
### <a name="the-debugger-cant-locate-the-correct-version-of-the-source-file-for-a-breakpoint"></a>Le débogueur ne peut pas localiser la bonne version du fichier source pour un point d’arrêt  
 Si un fichier source a été modifié et que la source ne correspond plus au code que vous déboguez, le débogueur peut rechercher le fichier source correspondant à un point d’arrêt, même si le fichier source existe.  
  
1.  Si vous voulez que Visual Studio affiche un code source qui ne correspond pas à la version que vous déboguez, choisissez **Déboguer/Options et paramètres**. Dans la page **Débogage/Général** , désactivez l’option **Les fichiers sources doivent correspondre exactement à la version d’origine** .  
  
2.  Vous pouvez aussi lier le point d’arrêt au fichier source. Sélectionnez le point d’arrêt et choisissez **Conditions** dans le menu contextuel. Cochez la case **Permettre que le code source soit différent de la version d’origine** dans la fenêtre **Paramètres de point d’arrêt** .  
  
### <a name="breakpoints-dont-work-in-a-dll"></a>Les points d’arrêt ne fonctionnent pas dans une DLL  
 Vous ne pouvez pas définir un point d’arrêt dans un fichier source si le débogueur n’a pas chargé les informations de débogage du module dans lequel le code est situé. L’affichage de messages tels que **le point d’arrêt ne sera pas défini**est l’un des symptômes possibles. Le glyphe du point d’arrêt d’avertissement s’affiche à l’emplacement du point d’arrêt. Cependant, ces points d’arrêt d’avertissement deviennent de véritables points d’arrêt une fois que le code est chargé. Pour plus d’informations sur le chargement de symboles, consultez [spécifier le symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)
