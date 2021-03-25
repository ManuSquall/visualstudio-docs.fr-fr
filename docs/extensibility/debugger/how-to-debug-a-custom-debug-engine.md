---
title: 'Comment : déboguer un moteur de débogage personnalisé | Microsoft Docs'
description: Découvrez les étapes qui vous permettent d’utiliser Visual Studio pour déboguer votre moteur de débogage personnalisé ou un type de projet personnalisé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ffd21fb08e920209d47ff66feb436f8a83aab53e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059923"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Comment : déboguer un moteur de débogage personnalisé
Un type de projet lance le moteur de débogage (DE) à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> méthode. Cela signifie que le DE est lancé sous le contrôle de l’instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contrôlant le type de projet. Toutefois, cette instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne peut pas déboguer le de. Les étapes suivantes vous permettent de déboguer votre personnalisé DE.

> [!NOTE]
> : Dans la procédure « déboguer un moteur de débogage personnalisé », vous devez attendre que le DE soit démarré avant de pouvoir s’y attacher. Si vous placez une boîte de message au début de votre, qui s’affiche quand le DE démarre, vous pouvez joindre à ce stade, puis effacer la boîte de message pour continuer. De cette façon, vous pouvez intercepter tous les événements.

> [!WARNING]
> Vous devez avoir installé le débogage distant avant d’essayer les procédures suivantes. Pour plus d’informations, consultez [débogage distant](../../debugger/remote-debugging.md) .

## <a name="debug-a-custom-debug-engine"></a>Déboguer un moteur de débogage personnalisé

1. Démarrez *msvsmon.exe*, Remote Debug Monitor.

2. Dans le menu **Outils** de *msvsmon.exe*, sélectionnez **options** pour ouvrir la boîte de dialogue **options** .

3. Sélectionnez l’option « aucune authentification », puis cliquez sur **OK**.

4. Démarrez une instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ouvrez votre projet personnalisé.

5. Démarrez une deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] et ouvrez votre projet personnalisé qui lance le (pour le développement, il s’agit généralement de la ruche de Registre expérimentale qui est configurée lors de l’installation de VSIP).

6. Dans cette deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , chargez un fichier source à partir de votre projet personnalisé et démarrez le programme à déboguer. Patientez quelques instants pour permettre au DE se charger ou patientez jusqu’à ce qu’un point d’arrêt soit atteint.

7. Dans la première instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (avec votre projet de), sélectionnez **attacher au processus** dans le menu **Déboguer** .

8. Dans la boîte de dialogue **attacher au processus** , définissez le **transport** sur **distant (natif uniquement sans authentification)**.

9. Remplacez le **qualificateur** par le nom de votre ordinateur (Remarque : il existe un historique des entrées, vous devez taper ce nom une seule fois).

10. Dans la liste **processus disponibles** , sélectionnez l’instance de que est en cours d’exécution, puis cliquez sur le bouton **attacher** .

11. Une fois que les symboles ont été chargés dans votre, placez les points d’arrêt dans votre code DE.

12. Chaque fois que vous arrêtez puis redémarrez le processus de débogage, répétez les étapes 6 à 10.

## <a name="debug-a-custom-project-type"></a>Déboguer un type de projet personnalisé

1. Démarrez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dans la ruche de Registre normale et chargez votre projet de type de projet (il s’agit de la source dans votre type de projet, et non d’une instanciation de votre type de projet).

2. Ouvrez les propriétés du projet et accédez à la page **Déboguer** . Pour la **commande**, tapez le chemin d’accès de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (par défaut, il s’agit de *[lecteur]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).

3. Pour les **arguments de commande**, tapez `/rootsuffix exp` pour la ruche expérimentale du Registre (créée lors de l’installation de VSIP).

4. Cliquez sur **OK** pour accepter les modifications.

5. Démarrez votre type de projet en appuyant sur **F5**. Une deuxième instance de est lancée [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

6. À ce stade, vous pouvez placer des points d’arrêt dans votre code source de type de projet.

7. Dans la deuxième instance de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , chargez ou créez une nouvelle instance de votre type de projet. Lors du chargement ou de la création, vos points d’arrêt peuvent être atteints.

8. Déboguez votre type de projet.

9. Si vous choisissez de déboguer le processus de lancement d’un DE, vous pouvez effectuer les étapes de la procédure « déboguer un moteur de débogage personnalisé » pour l’attacher à votre après son lancement. Cela vous donne trois instances de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en cours d’exécution : une pour votre type de projet source, une seconde pour votre type de projet instancié et un troisième attaché à votre.

## <a name="see-also"></a>Voir aussi
- [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)
