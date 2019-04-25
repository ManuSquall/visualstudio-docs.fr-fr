---
title: 'Procédure : Utilisez la fenêtre Pile des appels | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f40f5f27d603b67e6a7403f5327ffd89b486fa10
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60106451"
---
# <a name="how-to-use-the-call-stack-window"></a>Procédure : Utilisez la fenêtre Pile des appels
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fenêtre **Pile des appels** permet d’afficher les appels de fonctions ou de procédures actuellement dans la pile.  
  
 Le **pile des appels** fenêtre affiche le nom de chaque fonction et il est écrit dans le langage de programmation. Le nom de la fonction ou de la procédure peut être accompagné d'informations facultatives, telles qu'un nom de module et un numéro de ligne, ainsi que des noms, des valeurs et des types de paramètres. L'affichage de ces informations facultatives peut être activé ou désactivé.  
  
 Une flèche jaune identifie le frame de pile où le pointeur d'exécution se trouve actuellement. Par défaut, il s’agit du frame dont les informations apparaissent dans la source, **désassemblage**, **variables locales**, **espion**, et **automatique** windows. Si vous souhaitez modifier le contexte vers un autre frame sur la pile, vous pouvez le faire le **pile des appels** fenêtre.  
  
 Lorsque les symboles de débogage ne sont pas disponibles pour une partie d’une pile des appels, le **pile des appels** fenêtre ne peut pas être en mesure d’afficher des informations correctes pour cette partie de la pile des appels. La notation suivante apparaît :  
  
 [Les frames ci-dessous sont peut-être incorrects et/ou manquants, aucun symbole chargé pour name.dll]  
  
 Dans le code managé, par défaut. le **pile des appels** fenêtre masque les informations pour le code non-utilisateur. La notation suivante apparaît à la place des informations masquées :  
  
 **[\<Code externe >]**  
  
 Le code non-utilisateur est un code qui n'est pas « Mon code que vous pouvez choisir pour afficher les informations de la pile des appels pour le code non-utilisateur en utilisant le menu contextuel.  
  
 Le menu contextuel vous permet de choisir si vous voulez afficher les appels entre les threads.  
  
> [!NOTE]
>  Selon vos paramètres actifs ou votre édition, les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles qui sont décrites dans l'aide. Pour modifier vos paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>Pour afficher la fenêtre Pile des appels en mode arrêt ou en mode exécution  
  
- Sur le **déboguer** menu, sélectionnez **Windows** puis cliquez sur **pile des appels**.  
  
### <a name="to-change-the-optional-information-displayed"></a>Pour modifier l'affichage des informations facultatives  
  
- Cliquez sur le **pile des appels** fenêtre et activez ou désactivez **afficher \<**  _les informations que vous souhaitez_ **>**.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>Pour afficher les frames de code non-utilisateur dans la fenêtre Pile des appels  
  
- Cliquez avec le bouton droit sur la fenêtre **Pile des appels**, puis sélectionnez **Afficher le code externe**.  
  
### <a name="to-switch-to-another-stack-frame"></a>Pour basculer vers un autre frame de pile  
  
1. Dans le **pile des appels** fenêtre, cliquez sur le frame dont code et les données que vous souhaitez afficher.  
  
2. Sélectionnez **Basculer vers le frame**.  
  
     Une flèche verte avec extrémité recourbée apparaît à côté du frame sélectionné. Le pointeur d'exécution reste dans le frame d'origine, qui est toujours identifié par la flèche jaune. Si vous sélectionnez **Pas à pas** ou **Continuer** dans le menu **Déboguer**, l’exécution se poursuivra dans le frame d’origine, et non dans le frame sélectionné.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>Pour afficher des appels échangés avec d'autres threads  
  
- Cliquez avec le bouton droit sur la fenêtre **Pile des appels**, puis sélectionnez **Inclure les appels échangés avec d’autres threads**.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>Pour afficher le code source d'une fonction dans la pile des appels  
  
- Dans la fenêtre **Pile des appels**, cliquez avec le bouton droit sur la fonction dont vous voulez afficher le code source, puis sélectionnez **Atteindre le code source**.  
  
### <a name="to-visually-trace-the-call-stack"></a>Pour assurer le suivi visuel de la pile des appels  
  
1. Dans la fenêtre **Pile des appels**, ouvrez le menu contextuel. Choisissez **afficher la pile des appels sur carte de Code**. (Clavier : **CTRL** + **MAJ** + **`**)  
  
     Consultez [mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Pour afficher le code machine d'une fonction dans la pile des appels  
  
- Dans la fenêtre **Pile des appels**, cliquez avec le bouton droit sur la fonction dont vous voulez afficher le code machine, puis sélectionnez **Atteindre le code machine**.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>Pour exécuter jusqu'à une fonction spécifique de la fenêtre Pile des appels  
  
- Dans le **pile des appels** fenêtre, sélectionnez la fonction, avec le bouton droit et choisissez **exécuter jusqu’au curseur**.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Pour définir un point d'arrêt sur le point de sortie d'un appel de fonction  
  
- Consultez [définir un point d’arrêt à une fonction de pile d’appel](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).  
  
### <a name="to-load-symbols-for-a-module"></a>Charger les symboles d'un module  
  
- Dans le **pile des appels** fenêtre, cliquez sur le frame qui affiche le module dont les symboles vous souhaitez recharger et sélectionnez **charger les symboles**.  
  
## <a name="loading-symbols"></a>Chargement de symboles  
 Dans la fenêtre **Pile des appels**, vous pouvez charger des symboles de débogage pour du code qui ne possède actuellement aucun symbole chargé. Ces symboles peuvent être des symboles .NET Framework ou système téléchargés à partir des serveurs de symboles publics de Microsoft ou des symboles situés dans un chemin d’accès aux symboles sur l’ordinateur que vous déboguez.  
  
 Consultez [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols"></a>Pour charger des symboles  
  
1. Dans le **pile des appels** fenêtre, avec le bouton droit le frame pour lequel des symboles ne sont pas chargés. La frame est alors grisée.  
  
2. Pointez sur **charger les symboles depuis** puis cliquez sur **serveurs de symboles Microsoft** ou **chemin des symboles**.  
  
#### <a name="to-set-the-symbol-path"></a>Pour définir le chemin d'accès aux symboles  
  
1. Dans la fenêtre **Pile des appels**, choisissez **Paramètres des symboles** dans le menu contextuel.  
  
     La boîte de dialogue **Options** s’ouvre et la page **Symboles** s’affiche.  
  
2. Cliquez sur **paramètres des symboles**.  
  
3. Dans la boîte de dialogue **Options**, cliquez sur l’icône de dossier.  
  
     Un curseur apparaît dans la zone **Emplacements du fichier de symboles (.pdb)**.  
  
4. Tapez un chemin d’accès au répertoire correspondant à l’emplacement de symboles sur l’ordinateur que vous déboguez. En cas de débogage local, il s'agit de votre ordinateur local. Dans le cadre d'un débogage distant, il s'agit de l'ordinateur distant.  
  
5. Cliquez sur **OK** pour fermer la boîte de dialogue **Options**.  
  
## <a name="see-also"></a>Voir aussi  
 [Code mixte et informations manquantes dans la fenêtre Pile des appels](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Guide pratique pour Modifier le Format numérique de débogueur Windows](http://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Spécifier les fichiers de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)
