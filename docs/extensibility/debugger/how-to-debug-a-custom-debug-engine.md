---
title: 'Comment: Debug un moteur Debug personnalisé (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79790bfc9c9cd3767a453258b8c2d340f64d029
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738578"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Comment: Débogé d’un moteur de débogé personnalisé
Un type de projet lance le moteur <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> de débogé (DE) de la méthode. Cela signifie que le DE est lancé [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sous le contrôle de l’instance de contrôle du type de projet. Toutefois, cette [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instance de ne peut pas déboiffer le DE. Ce qui suit sont les étapes qui vous permettent de déboiffer votre DE personnalisé.

> [!NOTE]
> : Dans la procédure "Debug un moteur de débogé personnalisé", vous devez attendre que le DE commence avant de pouvoir s’y attacher. Si vous placez une boîte de message près du début de votre DE qui s’affiche lorsque le DE commence, vous pouvez attacher à ce point, puis effacer la boîte de message pour continuer. De cette façon, vous pouvez attraper tous les événements DE.

> [!WARNING]
> Vous devez avoir débogage à distance installé avant de tenter les procédures suivantes. Voir [le débogage à distance](../../debugger/remote-debugging.md) pour plus de détails.

## <a name="debug-a-custom-debug-engine"></a>Debug un moteur de débogé personnalisé

1. Démarrer *msvsmon.exe*, le moniteur Debug à distance.

2. Du menu **Tools** dans *msvsmon.exe*, sélectionnez **Options** pour ouvrir la boîte de dialogue **Options.**

3. Sélectionnez l’option "pas d’authentification" et cliquez **sur OK**.

4. Démarrez une [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instance et ouvrez votre projet DE personnalisé.

5. Démarrez une [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deuxième instance de et ouvrez votre projet personnalisé qui lance le DE (pour le développement, c’est généralement dans la ruche de registre expérimental qui est mis en place lorsque VSIP est installé).

6. Dans ce deuxième [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]cas de , charger un fichier source de votre projet personnalisé et commencer le programme à déboçonner. Attendez quelques instants pour permettre au DE de charger, ou attendez jusqu’à ce qu’un point d’arrêt soit touché.

7. Dans le premier [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] cas de (avec votre projet DE), **sélectionnez Attach to Process** à partir du menu **Debug.**

8. Dans la boîte de dialogue **Attach to Process,** changez le **transport** à **distance (autochtone seulement sans authentification).**

9. Changez le **qualificatif** au nom de votre machine (note : il y a une histoire d’entrées, donc vous n’avez besoin de taper ce nom qu’une seule fois).

10. Dans la liste **des processus disponibles,** sélectionnez l’instance de votre DE qui est en cours d’exécution et cliquez sur le bouton **Joindre.**

11. Une fois que les symboles ont chargé dans votre DE, placez les points d’arrêt dans votre code DE.

12. Chaque fois que vous vous arrêtez, puis redémarrez le processus de débogage, répétez les étapes 6 à 10.

## <a name="debug-a-custom-project-type"></a>Debug un type de projet personnalisé

1. Commencez [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dans la ruche normale de registre et chargez votre projet de type projet (c’est-à-dire la source de votre type de projet, pas une instantanéisation de votre type de projet).

2. Ouvrez les propriétés du projet et rendez-vous sur la page **Debug.** Pour la **commande**, tapez le chemin vers l’IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] défaut, il *s’agit de [drive]*'Program Files’Microsoft 8'Common7'IDE’devenv.exe).

3. Pour les arguments `/rootsuffix exp` de **commande**, tapez pour la ruche expérimentale de registre (créé lors de l’installation du VSIP).

4. Cliquez sur **OK** pour accepter les modifications.

5. Démarrez votre type de projet en appuyant sur **F5**. Cela lance une [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]deuxième instance de .

6. À ce stade, vous pouvez placer des points d’arrêt dans votre code source de type projet.

7. Dans le second [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]cas, chargez ou créez une nouvelle instance de votre type de projet. Pendant la charge ou la création, vos points d’arrêt peuvent être touchés.

8. Débogéez votre type de projet.

9. Si vous choisissez de déboiffer le processus de lancement d’un DE, vous pouvez effectuer les étapes de la procédure "Debug un moteur de débogé personnalisé" à attacher à votre DE après son lancement. Cela vous donne [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] trois instances de fonctionnement: une pour votre source de type de projet, une seconde pour votre type de projet instantané, et une troisième attachée à votre DE.

## <a name="see-also"></a>Voir aussi
- [Création d’un moteur de débogé personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)
