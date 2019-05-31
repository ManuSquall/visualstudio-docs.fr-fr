---
title: 'Procédure : Déboguer un moteur de débogage personnalisé | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 992440dd137b5622f4c619f1f81008eb38e1ff5f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334826"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Procédure : Déboguer un moteur de débogage personnalisé
Un type de projet lance le moteur de débogage (dé) à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> (méthode). Cela signifie que l’Allemagne est démarrée sous le contrôle de l’instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contrôle du type de projet. Toutefois, cette instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne peut pas déboguer le DE. Voici les étapes qui vous permettent de déboguer votre DE personnalisé.

> [!NOTE]
> :     Dans la procédure « Déboguer un moteur de débogage personnalisé », vous devez attendre le DE démarrer avant que vous pouvez attacher à celui-ci. Si vous placez une boîte de message au début de votre DE qui s’affiche au démarrage de l’Allemagne, vous pouvez attacher à ce stade, puis désactivez la boîte de message pour continuer. De cette façon, vous pouvez intercepter tous les événements de l’Allemagne.

> [!WARNING]
> Vous devez disposer de débogage à distance est installé avant d’essayer les procédures suivantes. Consultez [le débogage à distance](../../debugger/remote-debugging.md) pour plus d’informations.

## <a name="debug-a-custom-debug-engine"></a>Déboguer un moteur de débogage personnalisé

1. Démarrer *msvsmon.exe*, moniteur de débogage distant.

2. À partir de la **outils** menu *msvsmon.exe*, sélectionnez **Options** pour ouvrir le **Options** boîte de dialogue.

3. Sélectionnez l’option « Aucune authentification » et cliquez sur **OK**.

4. Démarrer une instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ouvrez votre projet DE personnalisé.

5. Démarrez une deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ouvrez votre projet personnalisé qui lance l’Allemagne (pour le développement, il s’agit généralement de la ruche expérimentale du Registre qui est configurée lorsque VSIP est installé).

6. Dans cette seconde instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], de charger un fichier source à partir de votre projet personnalisé et démarrer le programme à déboguer. Attendez quelques instants pour permettre le DE chargement, ou patientez jusqu'à ce qu’un point d’arrêt est atteint.

7. Dans la première instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (avec votre projet DE), sélectionnez **attacher au processus** à partir de la **déboguer** menu.

8. Dans le **attacher au processus** boîte de dialogue, choisissez le **Transport** à **distant (natif uniquement avec aucune authentification)** .

9. Modifier le **qualificateur** pour le nom de votre ordinateur (Remarque : il étant un historique des entrées, vous devez taper ce nom qu’une seule fois).

10. Dans le **processus disponibles** , sélectionnez l’instance de votre DE est en cours d’exécution et cliquez sur le **attacher** bouton.

11. Une fois les symboles ont chargé dans votre DE, placez des points d’arrêt dans votre code DE.

12. Chaque fois que vous arrêtez et redémarrez le processus de débogage, répétez les étapes 6 à 10.

## <a name="debug-a-custom-project-type"></a>Déboguer un type de projet personnalisé

1. Démarrer [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dans la ruche du Registre normal et charge votre projet tapez projet (il s’agit, la source à votre type de projet, et pas une instanciation de votre type de projet).

2. Ouvrez les propriétés du projet et accédez à la **déboguer** page. Pour le **commande**, tapez le chemin d’accès à la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (par défaut, il s’agit de *[lecteur]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).

3. Pour le **Arguments de commande**, type `/rootsuffix exp` pour la ruche expérimentale du Registre (créée lors de l’installation VSIP).

4. Cliquez sur **OK** pour accepter les modifications.

5. Démarrez votre type de projet en appuyant sur **F5**. Cette action lance une deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

6. À ce stade, vous pouvez placer des points d’arrêt dans votre code de source de type de projet.

7. Dans la deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], charger ou créer une nouvelle instance de votre type de projet. Pendant la création ou de charge, vos points d’arrêt peuvent être atteint.

8. Déboguer votre type de projet.

9. Si vous choisissez de déboguer le processus de lancement d’un DE, vous pouvez effectuer les étapes de la procédure « Déboguer un moteur de débogage personnalisé » pour attacher à votre DE après son lancement. Ainsi, vous avez trois instances de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en cours d’exécution : un pour votre source de type de projet, un autre pour votre type de projet instancié et un troisième attaché à votre DE.

## <a name="see-also"></a>Voir aussi
- [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)