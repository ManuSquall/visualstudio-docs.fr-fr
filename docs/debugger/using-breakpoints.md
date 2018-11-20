---
title: Utilisez des points d’arrêt dans le débogueur Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 02/07/2018
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
helpviewer_keywords:
- breakpoints, about breakpoints
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd522a5f5ff39814df3526843ae7d03578f92e86
ms.sourcegitcommit: 331dbb12e11fcd7f5d15fab05f3c861e48126e43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51826841"
---
# <a name="use-breakpoints-in-the-visual-studio-debugger"></a>Utilisez des points d’arrêt dans le débogueur Visual Studio
Points d’arrêt sont une des techniques de débogage plus importantes dans la boîte à outils du développeur de votre. Vous définissez des points d’arrêt là où vous souhaitez suspendre l’exécution du débogueur. Par exemple, vous souhaitez afficher l’état des variables de code ou examiner la pile des appels à un certain point d’arrêt. Si c’est la première fois que vous essayez de déboguer du code, vous pouvez lire [Débogage pour grands débutants](../debugger/debugging-absolute-beginners.md) avant de poursuivre cet article.
  
##  <a name="BKMK_Overview"></a> Ensemble des points d’arrêt dans le code source  
 Vous pouvez définir un point d’arrêt sur n’importe quelle ligne de code exécutable. Par exemple, dans le code c# suivant, vous pouvez définir un point d’arrêt sur la déclaration de variable, le `for` boucle ou code à l’intérieur de la `for` boucle. Vous ne pouvez pas définir un point d’arrêt sur les déclarations d’espace de noms ou une classe, ou sur la signature de méthode.  

 Pour définir un point d’arrêt dans le code source, cliquez dans la marge gauche en regard d’une ligne de code. Vous pouvez également sélectionner la ligne et appuyez sur **F9**, sélectionnez **déboguer** > **point d’arrêt**, ou avec le bouton droit et sélectionnez **point d’arrêt**  >  **Insérer le point d’arrêt**. Le point d’arrêt apparaît sous la forme d’un point rouge dans la marge de gauche.  
  
 ![Définissez un point d’arrêt](../debugger/media/basicbreakpoint.png "base point d’arrêt")  
  
 Lorsque vous déboguez, l’exécution s’arrête au point d’arrêt, avant l’exécution du code sur cette ligne. Le symbole de point d’arrêt affiche une flèche jaune. 

 Sur le point d’arrêt dans l’exemple suivant, la valeur de `testInt` est toujours 1.  
  
 ![L’exécution de point d’arrêt s’est arrêtée](../debugger/media/breakpointexecution.png "l’exécution du point d’arrêt")  
  
 Lorsque le débogueur s’arrête au point d’arrêt, vous pouvez consulter l’état actuel de l’application, y compris les valeurs des variables et la pile des appels. Pour plus d’informations sur la pile des appels, consultez [Comment : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md).  

- Le point d’arrêt est un bouton bascule. Vous pouvez cliquer dessus, appuyez sur **F9**, ou utilisez **déboguer** > **point d’arrêt** pour supprimer ou insérez-la à nouveau.
  
- Pour désactiver un point d’arrêt sans le supprimer, placez le curseur sur ou faites un clic droit et sélectionnez **désactiver le point d’arrêt**. Points d’arrêt désactivés apparaissent sous forme de points vides dans la marge de gauche ou la **des points d’arrêt** fenêtre. Pour réactiver un point d’arrêt, placez le curseur sur ou faites un clic droit et sélectionnez **activer le point d’arrêt**. 
  
- Définir des conditions et actions, ajouter et modifier les étiquettes ou exporter un point d’arrêt en cliquant et en sélectionnant la commande appropriée, ou pointant dessus et en sélectionnant le **paramètres** icône.

##  <a name="BKMK_Set_a_breakpoint_in_a_function"></a> Définissez des points d’arrêt du débogueur windows 

Vous pouvez également définir des points d’arrêt à partir de la **pile des appels** et **désassemblage** fenêtres du débogueur.  
  
### <a name="BKMK_Set_a_breakpoint_in_the_call_stack_window"></a> Définir un point d’arrêt dans la fenêtre Pile des appels  

 Pour vous arrêter à l’instruction ou de la ligne à laquelle une fonction appelante retourne à, vous pouvez définir un point d’arrêt dans le **pile des appels** fenêtre. 
  
**Pour définir un point d’arrêt dans la fenêtre Pile des appels :**

1. Pour ouvrir le **pile des appels** fenêtre, vous devez être suspendus pendant le débogage. Sélectionnez **déboguer** > **Windows** > **pile des appels**, ou appuyez sur **Ctrl** + **Alt**+**C**.  
   
2. Dans le **pile des appels** fenêtre, cliquez sur la fonction d’appel et sélectionnez **point d’arrêt** > **insérer un point d’arrêt**, ou appuyez sur **F9**.  
   
   Un symbole de point d’arrêt apparaît en regard du nom d’appel de fonction dans la marge gauche de la pile des appels.
   
Le point d’arrêt de la pile des appels s’affiche dans le **des points d’arrêt** fenêtre en tant qu’adresse, avec un emplacement de mémoire qui correspond à la prochaine instruction exécutable de la fonction. 

Le débogueur s’arrête au niveau de l’instruction.  

Pour plus d’informations sur la pile des appels, consultez [Comment : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md). 

À visuellement trace des points d’arrêt pendant l’exécution de code, consultez [mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md). 
  
### <a name="set-a-breakpoint-in-the-disassembly-window"></a>Définir un point d’arrêt dans la fenêtre code machine  
   
1. Pour ouvrir le **désassemblage** fenêtre, vous devez être suspendus pendant le débogage. Sélectionnez **déboguer** > **Windows** > **désassemblage**, ou appuyez sur **Alt** + **8**.  
   
2. Dans le **désassemblage** fenêtre, cliquez dans la marge gauche de l’instruction que vous souhaitez marquer un arrêt. Vous pouvez également sélectionner et appuyez sur **F9**, ou avec le bouton droit et sélectionnez **point d’arrêt** > **insérer un point d’arrêt**. 

##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Points d’arrêt de jeu (fonction)  

  Vous pouvez arrêter l’exécution lorsqu’une fonction est appelée. 

**Pour définir un point d’arrêt de fonction :**
  
1. Sélectionnez **déboguer** > **nouveau point d’arrêt** > **point d’arrêt de la fonction**, ou appuyez sur **Alt** + **F9** > **Ctrl**+**B**. 
   
   Vous pouvez également sélectionner **New** > **point d’arrêt de la fonction** dans le **des points d’arrêt** fenêtre.
   
1. Dans le **nouveau point d’arrêt de la fonction** boîte de dialogue, entrez le nom de fonction dans le **nom de la fonction** boîte. 

   Pour affiner la spécification de fonction :
   
   - Utilisez le nom de fonction qualifié complet. 
     
     Exemple :  `Namespace1.ClassX.MethodA()`
     
   - Ajouter les types de paramètre d’une fonction surchargée. 
     
     Exemple :  `MethodA(int, string)`
     
   - Utilisez le ' !' symbole pour spécifier le module.
     
     Exemple : `App1.dll!MethodA`
     
   - Utilisez l’opérateur de contexte en C++ natif.
     
     `{function, , [module]} [+<line offset from start of method>]`
     
     Exemple : `{MethodA, , App1.dll}+2`
   
1. Dans le **langage** liste déroulante, choisissez la langue de la fonction.
   
1. Sélectionnez **OK**.
  
### <a name="set-a-function-breakpoint-using-a-memory-address-native-c-only"></a>Définissez un point d’arrêt de fonction à l’aide d’une adresse de mémoire (C++ natif uniquement)  
 Vous pouvez utiliser l’adresse d’un objet pour définir un point d’arrêt de la fonction sur une méthode appelée par une instance spécifique d’une classe.  Par exemple, étant donné un objet de type `my_class`, vous pouvez définir un point d’arrêt de fonction sur le `my_method` méthode qui appelle l’instance. 
  
1.  Définissez un point d’arrêt quelque part après l’instanciation de l’instance de la classe.  
    
2.  Rechercher l’adresse de l’instance (par exemple, `0xcccccccc`). 
    
3.  Sélectionnez **déboguer** > **nouveau point d’arrêt** > **point d’arrêt de la fonction**, ou appuyez sur **Alt** + **F9** > **Ctrl**+**B**.  
    
4.  Ajoutez le code suivant à la **nom de la fonction** zone, puis sélectionnez **C++** langage.  
    
    ```C++  
    ((my_class *) 0xcccccccc)->my_method  
    ```  

## <a name="BKMK_set_a_data_breakpoint_native_cplusplus_only"></a>Définir des points d’arrêt de données (natif C++ uniquement) 
 
 Arrêt sur variable interrompre l’exécution quand une valeur stockée à une adresse mémoire spécifiée change. Si la valeur est lue mais pas modifiée, l’exécution ne s’interrompt pas.  
  
**Pour définir un point d’arrêt de données :**

1.  Dans un projet C++, démarrez le débogage et attendez qu’un point d’arrêt est atteint. Sur le **déboguer** menu, choisissez **nouveau point d’arrêt** > **point d’arrêt** 

    Vous pouvez également sélectionner **New** > **point d’arrêt** dans le **des points d’arrêt** fenêtre.
  
2.  Dans le **adresse** , tapez une adresse mémoire ou une expression qui correspond à une adresse mémoire. Par exemple, tapez `&avar` pour interrompre l’exécution quand le contenu de la variable `avar` change.  
  
3.  Dans la zone déroulante **Nombre d’octets** , sélectionnez le nombre d’octets que le débogueur doit surveiller. Par exemple, si vous sélectionnez **4**, le débogueur surveille les quatre octets à partir de `&avar` et interrompt l’exécution si l’un de ces octets change de valeur.  

Points d’arrêt de données ne fonctionnent pas dans les conditions suivantes :  
-   Un processus qui n’est pas en cours de débogage écrit dans l’emplacement de mémoire.  
-   L’emplacement de mémoire est partagé entre deux ou plusieurs processus.  
-   L’emplacement de mémoire est mis à jour dans le noyau. Par exemple, si la mémoire est transmise à la Windows 32 bits `ReadFile` (fonction), la mémoire sera mise à jour du mode noyau, donc le débogueur ne s’arrête sur la mise à jour.  

>[!NOTE]
>- Arrêt sur variable dépend d’adresses de mémoire spécifiques. L’adresse d’une variable change à partir d’une session de débogage à l’autre, des points d’arrêt de données sont automatiquement désactivés à la fin de chaque session de débogage.  
>  
>- Si vous définissez un point d’arrêt sur une variable locale, le point d’arrêt reste activé lorsque la fonction se termine, mais l’adresse de mémoire n’est plus applicable, par conséquent, le comportement du point d’arrêt est imprévisible. Si vous définissez un point d’arrêt sur une variable locale, vous devez supprimer ou désactiver le point d’arrêt avant la fin de la fonction.  

##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Gérer les points d’arrêt dans la fenêtre points d’arrêt 

 Vous pouvez utiliser la **des points d’arrêt** fenêtre pour afficher et gérer tous les points d’arrêt dans votre solution. Cet emplacement centralisé est particulièrement utile dans une solution de grande taille, ou pour des scénarios de débogage complexes où les points d’arrêt sont déterminants. 

Dans le **des points d’arrêt** fenêtre, vous pouvez rechercher, trier, filtrer, activer/désactiver ou supprimer des points d’arrêt. Vous pouvez également définir des conditions et les actions, ou ajouter une nouvelle fonction ou un point d’arrêt.
  
Pour ouvrir le **des points d’arrêt** fenêtre, sélectionnez **déboguer** > **Windows** > **des points d’arrêt**, ou appuyez sur  **ALT**+**F9** ou **Ctrl**+**Alt**+**B**.
  
![Fenêtre points d’arrêt](../debugger/media/breakpointswindow.png "fenêtre points d’arrêt")  
  
Pour sélectionner les colonnes à afficher dans le **des points d’arrêt** fenêtre, sélectionnez **afficher les colonnes**. Sélectionnez un en-tête de colonne pour trier la liste des points d’arrêt selon cette colonne. 

###  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Étiquettes de point d’arrêt  
Vous pouvez utiliser des étiquettes pour trier et filtrer la liste des points d’arrêt dans le **des points d’arrêt** fenêtre. 

1. Pour ajouter une étiquette à un point d’arrêt, cliquez sur le point d’arrêt dans le code source ou la **des points d’arrêt** fenêtre, puis **modifier les étiquettes**. Ajouter une nouvelle étiquette ou sélectionnez-en un déjà existant, puis sélectionnez **OK**.
2. Trier la liste de point d’arrêt dans le **des points d’arrêt** en sélectionnant le **étiquettes**, **Conditions**, ou les autres en-têtes de colonne. Vous pouvez sélectionner les colonnes à afficher en sélectionnant **afficher les colonnes** dans la barre d’outils. 
  
### <a name="export-and-import-breakpoints"></a>Exporter et importer les points d'arrêt  
 Pour enregistrer ou partager l’état et l’emplacement de vos points d’arrêt, vous pouvez exporter ou les importer. 

- Pour exporter un point d’arrêt dans un fichier XML, cliquez sur le point d’arrêt dans le code source ou **des points d’arrêt** , puis sélectionnez **exporter** ou **exportation sélectionnée**. Sélectionnez un emplacement d’exportation, puis **enregistrer**. L’emplacement par défaut est le dossier de solution. 
- Pour exporter plusieurs points d’arrêt, dans le **des points d’arrêt** fenêtre, sélectionnez les cases en regard des points d’arrêt, ou entrez les critères de recherche dans les **recherche** champ. Sélectionnez le **exporter tous les points d’arrêt correspondant aux critères de recherche actuel** icône, enregistrez le fichier. 
- Pour exporter tous les points d’arrêt, désactivez toutes les cases et laisser le **recherche** champ vide. Sélectionnez le **exporter tous les points d’arrêt correspondant aux critères de recherche actuel** icône, enregistrez le fichier.  
- Pour importer des points d’arrêt, dans le **des points d’arrêt** fenêtre, sélectionnez le **importer des points d’arrêt à partir d’un fichier** icône, accédez à l’emplacement du fichier XML, puis sélectionnez **Open**. 

##  <a name="breakpoint-conditions"></a>Conditions de point d’arrêt  
 Vous pouvez contrôler quand et où un point d’arrêt s’exécute en définissant des conditions. La condition peut être toute expression valide qui reconnaît le débogueur. Pour plus d’informations sur les expressions valides, consultez [Expressions dans le débogueur](../debugger/expressions-in-the-debugger.md).  

**Pour définir une condition de point d’arrêt :**

1. Cliquez sur le symbole de point d’arrêt et sélectionnez **Conditions**. Ou placez le curseur sur le symbole de point d’arrêt, sélectionnez le **paramètres** icône, puis sélectionnez **Conditions** dans le **les paramètres de point d’arrêt** fenêtre.  

   Vous pouvez également définir des conditions dans les **des points d’arrêt** fenêtre en double-cliquant sur un point d’arrêt et en sélectionnant **paramètres**, puis en sélectionnant **Conditions**. 
  
   ![Paramètres de point d’arrêt](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
2. Dans la liste déroulante, sélectionnez **Expression conditionnelle**, **nombre d’accès**, ou **filtre**et définissez la valeur en conséquence. 
  
3. Sélectionnez **fermer** ou appuyez sur **Ctrl**+**entrée** pour fermer la **les paramètres de point d’arrêt** fenêtre. Ou, à partir de la **des points d’arrêt** fenêtre, sélectionnez **OK** pour fermer la boîte de dialogue. 

Points d’arrêt avec un ensemble de conditions apparaissent avec un **+** symbole dans le code source et **des points d’arrêt** windows. 

<a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a>
### <a name="conditional-expression"></a>Expression conditionnelle

Lorsque vous sélectionnez **Expression conditionnelle**, vous pouvez choisir entre deux conditions : **vaut** ou **lorsque modifié**. Choisissez **vaut** pour arrêter l’exécution lorsque l’expression est satisfaite, ou **lorsque modifié** à arrêter quand la valeur de l’expression a changé.  
  
 Dans l’exemple suivant, le point d’arrêt est atteint uniquement lorsque la valeur de `testInt` est **4**:  
  
 ![Condition de point d’arrêt est true](../debugger/media/breakpointconditionistrue.png "point d’arrêt est la valeur true")  
  
 Dans l’exemple suivant, le point d’arrêt est atteint uniquement lorsque la valeur de `testInt` modifications :  
  
 ![Point d’arrêt lorsque modifié](../debugger/media/breakpointwhenchanged.png "point d’arrêt lorsque modifié")  
  
 Si vous définissez une condition de point d’arrêt dont la syntaxe est incorrecte, un message d’avertissement s’affiche. Si vous spécifiez une condition de point d’arrêt avec une syntaxe valide, mais dont la sémantique n’est pas valide, un message d’avertissement apparaît quand le point d’arrêt est atteint pour la première fois. Dans les deux cas, le débogueur s’arrête lorsqu’il atteint le point d’arrêt non valide. Le point d’arrêt n’est ignoré que si la condition est valide et prend la valeur `false`.  
  
 >[!NOTE]
 >Le comportement de la **lorsque modifié** champ est différent pour différents langages de programmation. 
 >- Pour le code natif, le débogueur ne considère pas la première évaluation de la condition comme étant une modification, donc n’atteint le point d’arrêt sur la première évaluation. 
 >- Pour le code managé, le débogueur atteint le point d’arrêt sur la première évaluation après **lorsque modifié** est sélectionné.  
  
### <a name="using-object-ids-in-conditional-expressions-c-and-f-only"></a>À l’aide des ID d’objet dans des expressions conditionnelles (C# et F# uniquement)  
 Il est parfois lorsque vous souhaitez observer le comportement d’un objet spécifique. Par exemple, vous souhaiterez peut-être savoir pourquoi un objet a été inséré dans une collection plusieurs fois. Dans C# et F#, vous pouvez créer des ID d’objet pour des instances spécifiques de [types référence](/dotnet/csharp/language-reference/keywords/reference-types)et les utiliser dans des conditions de point d’arrêt. L’ID d’objet est généré par les services de débogage du Common Language Runtime (CLR) et associé à l’objet.  

**Pour créer un ID d’objet :** 
  
1. Définissez un point d’arrêt dans le code un emplacement une fois que l’objet a été créé.  
   
2. Démarrez le débogage et lors de l’exécution s’arrête au point d’arrêt, sélectionnez **déboguer** > **Windows** > **variables locales** ou **Alt** + **4** pour ouvrir le **variables locales** fenêtre.
   
   Rechercher le point d’arrêt dans le **variables locales** fenêtre, faites un clic droit, puis sélectionnez **Make Object ID**.  
   
   Le symbole **$** et un nombre s’affichent alors dans la fenêtre **Variables locales** . Il s’agit de l’ID d’objet.  
   
3. Ajouter un nouveau point d’arrêt au point que vous voulez examiner ; par exemple, lorsque l’objet doit être ajouté à la collection. Cliquez sur le point d’arrêt et sélectionnez **Conditions**.  
   
4. Utiliser l’ID d’objet dans le **Expression conditionnelle** champ. Par exemple, si la variable `item` est l’objet à ajouter à la collection, sélectionnez **vaut** et type **item == $\<n >**, où \<n > est le numéro d’ID objet .  
   
   L’exécution s’arrête au point où cet objet doit être ajouté à la collection.  
   
   Pour supprimer l’ID d’objet, cliquez sur la variable dans le **variables locales** fenêtre et sélectionnez **supprimer l’ID objet**.  

>[!NOTE]
>Les ID d’objet créent des références faibles et n’empêchent pas l’objet de subir une récupération de mémoire. Leur validité ne vaut que pour la session de débogage active.  
  
### <a name="hit-count"></a>Nombre d’accès  
 Si vous pensez qu’une boucle dans votre code commence anormal après un certain nombre d’itérations, vous pouvez définir un point d’arrêt pour arrêter l’exécution une fois ce nombre de correspondances, plutôt que de devoir appuyez plusieurs fois sur **F5** pour atteindre cette itération.  
  
 Sous **Conditions** dans le **les paramètres de point d’arrêt** fenêtre, sélectionnez **nombre d’accès**, puis spécifiez le nombre d’itérations. Dans l’exemple suivant, le point d’arrêt est défini à atteindre à chaque autre itération :  
  
 ![Nombre d’accès de point d’arrêt](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
### <a name="filter"></a>Filtre  
Vous pouvez limiter le déclenchement d’un point d’arrêt seulement sur des appareils spécifiés ou dans des processus et des threads spécifiés.  
  
Sous **Conditions** dans le **les paramètres de point d’arrêt** fenêtre, sélectionnez **filtre**, puis entrez un ou plusieurs des expressions suivantes :  
  
-   MachineName = "nom"  
-   ProcessId = valeur  
-   ProcessName = "nom"  
-   ThreadId = valeur  
-   ThreadName = "nom"  

Placez les valeurs de chaîne entre guillemets doubles. Vous pouvez combiner des clauses à l’aide de `&` (AND), `||` (OR), `!` (NOT) et de parenthèses.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Actions de point d’arrêt et points de trace  
 Un *point de trace* est un point d’arrêt qui affiche un message dans le **sortie** fenêtre. Un point de trace peut faire office d’instruction de trace temporaire dans le langage de programmation.  
  
**Pour définir un point de trace :**

1. Cliquez sur un point d’arrêt et sélectionnez **Actions**. Ou, dans le **les paramètres de point d’arrêt** fenêtre, pointez sur le point d’arrêt, sélectionnez le **paramètres** icône, puis sélectionnez **Actions**.  
   
1. Entrez un message dans le **consigner le message dans la fenêtre sortie** champ. Le message peut contenir des chaînes de texte générique, les valeurs des variables ou des expressions entre accolades et spécificateurs de format ([c#](../debugger/format-specifiers-in-csharp.md) et [C++](../debugger/format-specifiers-in-cpp.md)) pour les valeurs.
   
   Vous pouvez également utiliser les mots clés spéciaux suivants dans le message :  
   
   - **$ADDRESS** -instruction actuelle  
   - **$CALLER** -nom de la fonction appelante  
   - **$CALLSTACK** -pile des appels 
   - **$FUNCTION** -nom de la fonction actuelle  
   - **$PID** -id de processus  
   - **$PNAME** -nom du processus  
   - **$TID** -id de thread  
   - **$TNAME** -nom de thread  
   - **$TICK** -nombre de cycles (à partir de Windows `GetTickCount`)  
   
1. Pour imprimer le message à la **sortie** fenêtre sans rupture, sélectionnez le **continuer l’exécution** case à cocher. Pour imprimer l’exécution de message et d’arrêt sur le point de trace, désactivez la case à cocher. 

Points de trace apparaissent sous forme de losanges rouge dans la marge gauche du code source et **des points d’arrêt** windows. 
  
## <a name="see-also"></a>Voir aussi  
 [Quel est le débogage ?](../debugger/what-is-debugging.md)  
 [Écrire de meilleures C# code à l’aide de Visual Studio](../debugger/write-better-code-with-visual-studio.md)  
 [Premier aperçu de débogage](../debugger/debugger-feature-tour.md)  
 [Résoudre les problèmes de points d’arrêt dans le débogueur Visual Studio](../debugger/troubleshooting-breakpoints.md)  
