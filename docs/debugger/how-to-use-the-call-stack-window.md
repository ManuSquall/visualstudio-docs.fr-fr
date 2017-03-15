---
title: "Comment&#160;: utiliser la fen&#234;tre Pile des appels | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.callstack"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "aspx"
helpviewer_keywords: 
  - "threads (Visual Studio), affichage des appels vers ou provenant de"
  - "fonctions (débogueur), affichage du code dans la pile des appels"
  - "code machine"
  - "point d’arrêts, fenêtre Pile des appels"
  - "débogage (Visual Studio), basculement vers un autre frame de pile"
  - "débogage (Visual Studio), fenêtre Pile des appels"
  - "Pile des appels (fenêtre), affichage du code source de fonctions dans la pile des appels"
  - "pile, basculement d’un frame à un autre"
  - "Pile des appels (fenêtre), affichage du code machine de fonctions dans la pile des appels"
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: utiliser la fen&#234;tre Pile des appels
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La fenêtre **Pile des appels** permet d'afficher les appels de fonctions ou de procédures actuellement dans la pile.  
  
 La fenêtre **Pile des appels** affiche le nom de chaque fonction et le langage de programmation dans lequel elle est écrite.  Le nom de la fonction ou de la procédure peut être accompagné d'informations facultatives, telles qu'un nom de module et un numéro de ligne, ainsi que des noms, des valeurs et des types de paramètres.  L'affichage de ces informations facultatives peut être activé ou désactivé.  
  
 Une flèche jaune identifie le frame de pile où le pointeur d'exécution se trouve actuellement.  Par défaut, il s'agit du frame dont les informations apparaissent dans les fenêtres sources **Code machine**, **Variables locales**, **Espion** et **Automatique**.  Si vous voulez changer le contexte en un autre frame sur la pile, vous pouvez le faire dans la fenêtre **Pile des appels**.  
  
 Lorsque les symboles de débogage ne sont pas disponibles pour une partie d'une pile des appels, la fenêtre **Pile des appels** peut ne pas être capable d'afficher des informations correctes pour cette partie de la pile des appels.  La notation suivante apparaît :  
  
 \[Les frames ci\-dessous sont peut\-être incorrects et\/ou manquants, aucun symbole chargé pour name.dll\]  
  
 En code managé, par défaut, la fenêtre **Pile des appels** masque les informations pour le code non\-utilisateur.  La notation suivante apparaît à la place des informations masquées :  
  
 **\[\<External Code\>\]**  
  
 Le code non\-utilisateur est un code qui n'est pas « Mon code que vous pouvez choisir pour afficher les informations de la pile des appels pour le code non\-utilisateur en utilisant le menu contextuel.  
  
 Le menu contextuel vous permet de choisir si vous voulez afficher les appels entre les threads.  
  
> [!NOTE]
>  Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide.  Pour modifier vos paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour afficher la fenêtre Pile des appels en mode arrêt ou en mode exécution  
  
-   Dans le menu **Déboguer**, sélectionnez **Fenêtres**, puis cliquez sur **Pile des appels**.  
  
### Pour modifier l'affichage des informations facultatives  
  
-   Cliquez avec le bouton droit sur la fenêtre **Pile des appels** et activez ou désactivez **Afficher \<***the information that you want***\>**.  
  
### Pour afficher les frames de code non\-utilisateur dans la fenêtre Pile des appels  
  
-   Cliquez avec le bouton droit sur la fenêtre **Pile des appels**, puis sélectionnez **Afficher le code externe** dans le menu contextuel.  
  
### Pour basculer vers un autre frame de pile  
  
1.  Dans la fenêtre **Pile des appels**, cliquez avec le bouton droit sur le frame dont vous voulez afficher le code et les données.  
  
2.  Sélectionnez **Basculer vers le frame**.  
  
     Une flèche verte avec extrémité recourbée apparaît à côté du frame sélectionné.  Le pointeur d'exécution reste dans le frame d'origine, qui est toujours identifié par la flèche jaune.  Si vous sélectionnez **Pas à pas** ou **Continuer** dans le menu **Débogage**, l'exécution se poursuivra dans le frame d'origine, et non dans le frame sélectionné.  
  
### Pour afficher des appels échangés avec d'autres threads  
  
-   Cliquez avec le bouton droit dans la fenêtre **Pile des appels**, puis sélectionnez **Inclure les appels échangés avec d'autres threads**.  
  
### Pour afficher le code source d'une fonction dans la pile des appels  
  
-   Dans la fenêtre **Pile des appels**, cliquez avec le bouton droit sur la fonction dont vous voulez afficher le code source, puis sélectionnez **Atteindre le code source**.  
  
### Pour assurer le suivi visuel de la pile des appels  
  
1.  Dans la fenêtre **Pile des appels**, ouvrez le menu contextuel.  Sélectionnez **Afficher la pile d'appels sur la carte du code**. \(raccourci : **CTRL** \+ **MAJ** \+ **\`**\)  
  
     Consultez [Mapper les méthodes sur la pile des appels tout en déboguant](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### Pour afficher le code machine d'une fonction dans la pile des appels  
  
-   Dans la fenêtre **Pile des appels**, cliquez avec le bouton droit sur la fonction dont vous voulez afficher le code machine, puis sélectionnez **Atteindre le code machine**.  
  
### Pour exécuter jusqu'à une fonction spécifique de la fenêtre Pile des appels  
  
-   Voir la rubrique sur [l'exécution d'un emplacement ou d'une fonction spécifié\(e\)](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Run_to_a_specified_location_or_function).  
  
### Pour définir un point d'arrêt sur le point de sortie d'un appel de fonction  
  
-   Consultez [Définir un point d'arrêt à une ligne source, une instruction d'assembly ou une fonction de pile des appels](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_at_a_source_line__assembly_instruction__or_call_stack_function_).  
  
### Charger les symboles d'un module  
  
-   Dans la fenêtre **Pile des appels**, cliquez avec le bouton droit sur le frame qui affiche le module dont vous voulez recharger les symboles, puis sélectionnez **Charger les symboles**.  
  
## Chargement de symboles  
 Dans la fenêtre **Pile des appels**, vous pouvez charger des symboles de débogage pour du code qui ne possède actuellement aucun symbole chargé.  Ces symboles peuvent être des symboles .NET Framework ou système téléchargés à partir des serveurs de symboles publics de Microsoft ou des symboles situés dans un chemin d'accès aux symboles sur l'ordinateur que vous déboguez.  
  
 Consultez [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
#### Pour charger des symboles  
  
1.  Dans la fenêtre **Pile des appels**, cliquez avec le bouton droit sur le frame pour lequel des symboles ne sont pas chargés.  La frame est alors grisée.  
  
2.  Pointez sur **Charger les symboles depuis** et cliquez sur **Serveur de symboles publics Microsoft** ou sur **Chemin d'accès aux symboles**.  
  
#### Pour définir le chemin d'accès aux symboles  
  
1.  Dans la fenêtre **Pile des appels**, choisissez **Paramètres des symboles** dans le menu contextuel.  
  
     La boîte de dialogue **Options** s'ouvre et la page **Symboles** s'affiche.  
  
2.  Cliquez sur **Paramètres des symboles**.  
  
3.  Dans la boîte de dialogue **Options**, cliquez sur l'icône de dossier.  
  
     Un curseur apparaît dans la zone **Emplacements du fichier de symboles \(.pdb\)**.  
  
4.  Tapez un chemin d'accès au répertoire correspondant à l'emplacement de symboles sur l'ordinateur que vous déboguez.  En cas de débogage local, il s'agit de votre ordinateur local.  Dans le cadre d'un débogage distant, il s'agit de l'ordinateur distant.  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue **Options**.  
  
## Voir aussi  
 [Code mixte et informations manquantes dans la fenêtre Pile des appels](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Comment : modifier le format numérique des fenêtres du débogueur](../Topic/How%20to:%20Change%20the%20Numeric%20Format%20of%20Debugger%20Windows.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Utilisation des points d'arrêt](../debugger/using-breakpoints.md)