---
title: "Page Compiler, Concepteur de projets (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesCompile"
helpviewer_keywords: 
  - "compilation, projets Visual Basic"
  - "compilation, options [Visual Basic]"
  - "compilateurs, options Visual Basic"
  - "compilation, instructions [Visual Basic]"
  - "options du compilateur, Visual Basic"
  - "Concepteur de projets, page Compiler"
  - "page Compiler dans le Concepteur de projets"
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 60
---
# Page Compiler, Concepteur de projets (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La page **Compiler** du Concepteur de projets vous permet de spécifier les instructions de compilation.  Vous pouvez également spécifier sur cette page les options avancées du compilateur et les événements pre\-build ou post\-build.  
  
 Pour accéder à la page **Compiler**, sélectionnez un nœud de projet \(pas le nœud **Solution** \) dans **Explorateur de solutions**.  Choisissez **Projet**, **Propriétés** dans la barre de menus.  Lorsque le Concepteur de projets apparaît, cliquez sur l'onglet **Compiler**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## Configuration et Plateforme  
 Les paramètres suivants vous permettent de sélectionner la configuration et la plateforme à afficher ou modifier.  
  
> [!NOTE]
>  Grâce aux configurations de build simplifiées, le système de projet détermine s'il faut générer une version debug ou release.  Par conséquent, les listes **Configuration** et **Plateforme** ne sont pas affichées.  Pour plus d'informations, consultez [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e).  
  
 **Configuration**  
 Spécifie les paramètres de configuration à afficher ou à modifier.  Les paramètres sont **Débogage** \(par défaut\), **Version finale** ou **Toutes les configurations**.  Pour plus d'informations, consultez [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e) et [Comment : créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md).  
  
 **Plateforme**  
 Spécifie les paramètres de plateforme à afficher ou à modifier.  Vous pouvez spécifier **Any CPU** \(valeur par défaut\), **x64**, ou **x86**.  Pour plus d'informations, consultez [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e).  
  
## Options de configuration du compilateur  
 Les paramètres suivants vous permettent de définir les options de configuration du compilateur.  
  
 **Chemin de sortie de la génération**  
 Spécifie l'emplacement des fichiers de sortie pour cette configuration de projet.  Entrez le chemin d'accès de la sortie de génération dans cette zone ou cliquez sur le bouton **Parcourir** pour sélectionner un chemin d'accès.  Notez que le chemin d'accès est relatif ; si vous entrez un chemin d'accès absolu, il sera enregistré comme relatif.  Le chemin par défaut est bin\\Debug\\ ou bin\\Release\\.  Pour plus d'informations, consultez [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e).  
  
 Grâce aux configurations de build simplifiées, le système de projet détermine s'il faut générer une version debug ou release.  Si vous cliquez sur la commande **Build** dans le menu **Déboguer** \(F5\), la génération est placée dans l'emplacement de débogage, indépendamment du **Chemin de sortie** spécifié.  Toutefois, avec la commande **Build** du menu **Générer**, elle est placée dans l'emplacement spécifié.  Pour plus d'informations, consultez [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e).  
  
 **Option Explicit**  
 Indique s'il faut autoriser la déclaration implicite de variables.  Sélectionnez **Activer** pour requérir une déclaration explicite des variables.  Cela entraîne le compilateur à signaler des erreurs si les variables ne sont pas déclarées avant leur utilisation.  Sélectionnez **Off** pour autoriser la déclaration implicite de variables.  
  
 Ce paramètre correspond à l'option du compilateur [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 Si un fichier de code source contient [Option Explicit Statement](/dotnet/visual-basic/language-reference/statements/option-explicit-statement), la valeur `On` ou `Off` de l'instruction remplace le paramètre **Option Explicit** sur la **page de compilation**.  
  
 Lorsque vous créez un nouveau projet, le paramètre **Option Explicit** de la **page Compiler** a la valeur du paramètre **Option Explicit** de la boîte de dialogue **Options**.  Pour afficher ou modifier le paramètre de cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**.  Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.  Le paramètre par défaut d'origine **Option Explicit** dans **Valeurs par défaut VB** est **Activé**.  
  
 Il n'est généralement pas recommandé de définir **Option Explicit** sur `Off`.  Vous risquez de mal orthographier un nom de variable dans un ou plusieurs emplacements, ce qui peut provoquer des résultats inattendus lors de l'exécution du programme.  
  
 **Option Strict**  
 Spécifie s'il faut appliquer la sémantique de type stricte.  Lorsque **Option Strict** a la valeur **On**, les conditions suivantes provoquent une erreur de compilation :  
  
-   Conversions restrictives implicites  
  
-   Liaison tardive  
  
-   Type implicite qui génère un type `Object`  
  
 Les erreurs de conversion restrictive implicite se produisent lorsqu'il y a une conversion de types de données implicite qui est une conversion restrictive.  Pour plus d'informations, consultez [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Implicit and Explicit Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) et [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).  
  
 Un objet a une liaison tardive lorsqu'il est assigné à une propriété ou à une méthode d'une variable déclarée comme étant de type `Object`.  Pour plus d'informations, consultez [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement) et [Early and Late Binding](/dotnet/visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding).  
  
 Les erreurs de type d'objet implicite se produisent lorsqu'un type approprié ne peut pas être déduit pour une variable déclarée, de sorte qu'un type `Object` est déduit.  Cela se produit essentiellement lorsque vous utilisez une instruction `Dim` pour déclarer une variable sans utiliser une clause `As` et que `Option Infer` est désactivé.  Pour plus d'informations, consultez [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement), [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement) et [Visual Basic Language Specification](/dotnet/visual-basic/reference/language-specification).  
  
 Le paramètre **Option Strict** correspond à l'option du compilateur [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
 Si un fichier de code source contient [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement), la valeur `On` ou `Off` de l'instruction remplace le paramètre **Option Strict** sur la **page de compilation**.  
  
 Lorsque vous créez un projet, le paramètre **Option Strict** de la **page Compiler** a la valeur du paramètre **Option Strict** de la boîte de dialogue **Options**.  Pour afficher ou modifier le paramètre de cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**.  Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.  Le paramètre par défaut d'origine **Option Strict** dans **Valeurs par défaut VB** est **Désactivé**.  
  
 **Avertissements individuels Option Strict.** La section **Configurations des avertissements** de la **Page Compiler** contient des paramètres qui correspondent aux trois conditions qui provoquent une erreur de compilation lorsque `Option Strict` est activé.  Vous trouverez ci\-dessous ces paramètres :  
  
-   **Conversion implicite**  
  
-   **Liaison tardive ; l'appel pourrait échouer lors de l'exécution**  
  
-   **Type implicite ; objet supposé**  
  
 Lorsque vous affectez la valeur **On** à **Option Strict**, chacun de ces trois paramètres de configuration d'avertissement prend la valeur **Erreur**.  Lorsque vous affectez la valeur **Off** à **Option Strict**, chacun des trois paramètres prend la valeur **Aucun**.  
  
 Vous pouvez remplacer individuellement chaque paramètre de configuration d'avertissement par **Aucun**, **Avertissement** ou **Erreur**.  Si les trois paramètres de configuration de l'avertissement sont définis sur **Erreur**, `On` apparaît dans la zone `Option strict`.  Si les trois sont définis sur **None**, `Off` apparaît dans cette zone.  Pour toute autre combinaison de ces paramètres, **\(personnalisé\)** apparaît.  
  
 **Option Compare**  
 Spécifie le type de comparaison de chaînes à utiliser.  Sélectionnez **Binaire** pour indiquer au compilateur d'utiliser des comparaisons de chaînes binaires respectant la casse.  Sélectionnez **Text** pour utiliser des comparaisons de chaînes de texte spécifiques aux paramètres régionaux, qui ne respectent pas la casse.  
  
 Ce paramètre correspond à l'option du compilateur [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
 Si un fichier de code source contient [Option Compare Statement](/dotnet/visual-basic/language-reference/statements/option-compare-statement), la valeur `Binary` ou `Text` de l'instruction remplace le paramètre **Option Compare** sur la **page de compilation**.  
  
 Lorsque vous créez un projet, le paramètre **Option Compare** de la **page Compiler** a la valeur du paramètre **Option Compare** de la boîte de dialogue **Options**.  Pour afficher ou modifier le paramètre de cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**.  Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.  Le paramètre par défaut d'origine de **Option Compare** dans **Valeurs par défaut VB** est **Binaire**.  
  
 **Option infer**  
 Indique s'il faut autoriser l'inférence de type local dans les déclarations de variable.  Sélectionnez **Activer** pour permettre l'utilisation de l'inférence de type locale.  Sélectionnez **Off** pour bloquer l'inférence de type local.  
  
 Ce paramètre correspond à l'option du compilateur [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
 Si un fichier de code source contient [Option Infer Statement](/dotnet/visual-basic/language-reference/statements/option-infer-statement), la valeur `On` ou `Off` de l'instruction remplace le paramètre **Option Infer** sur la **page de compilation**.  
  
 Lorsque vous créez un projet, le paramètre **Option Infer** de la **page Compiler** a la valeur du paramètre **Option Infer** de la boîte de dialogue **Options**.  Pour afficher ou modifier le paramètre de cette boîte de dialogue, cliquez sur **Options** dans le menu **Outils**.  Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**.  Le paramètre par défaut d'origine **Option Infer** dans **Valeurs par défaut VB** est **Activé**.  
  
 **CPU cible**  
 Spécifie le processeur devant être ciblé par le fichier de sortie.  Spécifiez **x86** pour tout processeur Intel\- compatible de 32 bits, **x64** pour tout processeur Intel\- compatible avec les architectures 64 bits, **ARM** pour tout processeur de ARM, ou **Any CPU** pour spécifier que tout processeur est acceptable.  **Any CPU** est la valeur par défaut pour les nouveaux projets car elle permet à l'application de s'exécuter sur le plus grand nombre de types de matériel.  
  
 Pour plus d'informations, consultez [\/platform](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
 **Choix de 32 bits**  
 Si la case à cocher **Prefer32\-bit** est sélectionnée, l'application s'exécute comme une application 32 bits sur les versions de Windows 32 bits et 64 bits.  Sinon, l'application s'exécute comme une application 32 bits sur les versions 32 bits de windows et comme une application 64 bits sur les versions 64 bits de Windows.  
  
 Exécuter comme une application 64 bits double la taille du pointeur, et elle peut provoquer des problèmes de compatibilité avec les bibliothèques qui sont exclusivement de 32 bits.  Il est logique d'exécution d'une application comme 64 bits uniquement si elle s'exécute beaucoup plus rapide ou a besoin de plus de 4 Go de mémoire.  
  
 Cette case à cocher est disponible uniquement si toutes les conditions suivantes sont remplies :  
  
-   Dans **Page de compilation**, la liste **Unité centrale cible** a la valeur **Any CPU**.  
  
-   Dans **Page Application**, la liste **Type d'application** spécifie que le projet est une application.  
  
-   Dans **Page Application**, la liste **Framework cible** spécifie le .NET Framework 4,5.  
  
 **Configurations des avertissements**  
 Ce tableau répertorie les conditions de génération et le niveau de notification correspondant : **Aucun**, **Avertissement** ou **Erreur**.  
  
 Par défaut, tous les avertissements du compilateur sont ajoutés à la liste des tâches pendant la compilation.  Sélectionnez **Désactiver tous les avertissements** pour indiquer au compilateur de ne pas publier d'avertissements ou d'erreurs.  Sélectionnez **Considérer tous les avertissements comme des erreurs** si vous souhaitez que le compilateur traite les avertissements comme des erreurs devant être résolues.  
  
 **Désactiver tous les avertissements**  
 Indique s'il faut autoriser le compilateur à publier des notifications comme indiqué dans le tableau **Condition et notification** décrit précédemment dans ce document.  Cette case à cocher est désactivée par défaut.  Activez cette case à cocher pour demander au compilateur de ne pas publier d'avertissements ou d'erreurs.  
  
 Ce paramètre correspond à l'option du compilateur [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).  
  
 **Considérer tous les avertissements comme des erreurs**  
 Spécifie comment traiter les avertissements.  Par défaut, cette case à cocher est désactivée afin que toutes les notifications d'avertissement continuent à avoir la valeur **Avertissement**.  Activez cette case à cocher pour modifier toutes les notifications d'avertissement sur **Erreur**.  
  
 Cette option est disponible uniquement si **Désactiver tous les avertissements** est désactivé.  
  
 **Générer le fichier de documentation XML**  
 Spécifie s'il faut générer des informations de documentation.  Par défaut, cette case à cocher est activée pour demander au compilateur de générer des informations de documentation et de les placer dans un fichier XML.  Désactivez cette case à cocher pour indiquer au compilateur de ne pas créer de documentation.  
  
 Ce paramètre correspond à l'option du compilateur [\/doc](/dotnet/visual-basic/reference/command-line-compiler/doc).  
  
 **Inscrire pour COM Interop**  
 Spécifie si votre application managée expose un objet COM \(wrapper CCW\) qui permet à un objet COM d'interagir avec l'application.  
  
 Par défaut, cette case à cocher est désactivée pour spécifier que l'application n'autorisera pas COM Interop.  Activez cette case à cocher pour autoriser COM Interop.  
  
 Cette option n'est pas disponible pour les projets Application Windows ou Application Console.  
  
 **Événements de build**  
 Cliquez sur ce bouton pour accéder à la boîte de dialogue **Événements de build**.  Utilisez cette boîte de dialogue pour spécifier les instructions de configuration pre\-build et post\-build du projet.  Cette boîte de dialogue s'applique uniquement aux projets Visual Basic.  Pour plus d'informations, consultez [Événements de build, boîte de dialogue \(Visual Basic\)](../../ide/reference/build-events-dialog-box-visual-basic.md).  
  
 **Options avancées de compilation**  
 Cliquez sur ce bouton pour accéder à la boîte de dialogue **Paramètres avancés** du **compilateur**.  Utilisez la boîte de dialogue **Paramètres avancés** du **compilateur** pour spécifier les propriétés de configuration de build avancées d'un projet.  Cette boîte de dialogue s'applique uniquement aux projets Visual Basic.  Pour plus d'informations, consultez [Paramètres avancés du compilateur, boîte de dialogue \(Visual Basic\)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).  
  
## Voir aussi  
 [Debug and Release Project Configurations](http://msdn.microsoft.com/fr-fr/0440b300-0614-4511-901a-105b771b236e)   
 [Managing Compilation Properties](http://msdn.microsoft.com/fr-fr/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Comment : spécifier des événements de build \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Visual Basic Command\-Line Compiler](/dotnet/visual-basic/reference/command-line-compiler/index)   
 [Comment : créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md)