---
description: Vous n'êtes pas autorisé à inspecter l'identité du processus.
title: Vous n’êtes pas autorisé à inspecter l' &apos; identité du processus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2070f6734c667f64cb54e2c5fead8eb63fd50d2c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146221"
---
# <a name="error-you-do-not-have-permission-to-inspect-the-process39s-identity"></a>Erreur : vous n’êtes pas autorisé à inspecter l’identité du processus&#39;s
Vous n'êtes pas autorisé à inspecter l'identité du processus. Cela peut être dû à la configuration de votre système.

 Le débogueur n'a pas pu inspecter l'identité du processus, qui contient des informations nécessaires au débogage. La cause la plus probable est la désactivation des services Terminal Server. Les services Terminal Server sont activés par défaut. Pour les réactiver, procédez comme suit.

### <a name="to-enable-terminal-services"></a>Pour activer les services Terminal Server

1. Cliquez sur **Démarrer** , puis sur **panneau de configuration**.

2. Dans le panneau de configuration, choisissez **basculer vers l’affichage classique**, si nécessaire, puis double-cliquez sur **Outils d’administration**.

3. Dans la fenêtre **Outils d’administration**, double-cliquez sur **Gestion de l’ordinateur**.

4. Dans la fenêtre Gestion de l’ordinateur, développez le nœud **Services et applications**.

5. Sous **Services et applications**, cliquez sur **Services**.

     Une liste de services apparaît dans le volet droit.

6. Dans la liste **Services**, cliquez avec le bouton droit sur **Services Terminal Server**, puis choisissez **Propriétés**.

7. Dans la fenêtre **Propriétés des services Terminal Server** , accédez à l’onglet **général** et définissez **type de démarrage** sur **Manuel**.

8. Cliquez sur **OK**.

9. Redémarrez l'ordinateur.

     Cette procédure n'active pas automatiquement le Bureau à distance. Pour activer le Bureau à distance sur votre ordinateur, effectuez la procédure supplémentaire suivante.

### <a name="to-enable-remote-desktop"></a>Pour activer le Bureau à distance

1. Cliquez sur **Démarrer**, puis cliquez avec le bouton droit sur **Poste de travail**.

2. Choisissez **Propriétés**.

     La fenêtre **Propriétés système** s’affiche.

3. Cliquez sur **Distant**.

4. Sous **Bureau à distance**, sélectionnez **Autoriser les utilisateurs à se connecter à distance à cet ordinateur**.

5. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
- [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)
