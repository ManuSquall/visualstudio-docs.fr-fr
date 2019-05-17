---
title: 'Procédure : Déboguer une source .NET Framework | Microsoft Docs'
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 25f40b0528b794863aabdb13ed9785d2b0c551b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894272"
---
# <a name="how-to-debug-net-framework-source"></a>Procédure : Déboguer une source .NET Framework

Pour déboguer une source .NET Framework, vous devez :

- Activer le pas à pas détaillé dans la source du .NET Framework.

- Ont accès aux symboles de débogage pour le code.

  Vous pouvez choisir télécharger immédiatement les symboles de débogage, ou définir des options pour le téléchargement plus tard. Si vous ne pas télécharger des symboles immédiatement, ils allez télécharger la prochaine fois que vous démarrez le débogage de votre application. Pendant le débogage, vous pouvez également utiliser le **Modules** ou **pile des appels** windows pour télécharger et charger des symboles.

### <a name="to-enable-stepping-into-net-framework-source"></a>Pour activer le pas à pas détaillé dans la source de .NET Framework

1. Sous **outils** (ou **déboguer**) > **Options** > **débogage** > **général**, sélectionnez **source activer .NET Framework pas à pas détaillé**.

   - Si l'option Uniquement mon code était activée, une boîte de dialogue d'avertissement s'affiche pour signaler que cette option est à présent désactivée. Sélectionnez **OK**.

   - Si vous ne pas un cache de symboles local défini, une boîte de dialogue d’avertissement vous indique qu’un cache de symboles par défaut a été défini. Sélectionnez **OK**.

1. Sélectionnez **OK** pour fermer la **Options** boîte de dialogue.

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Pour définir ou modifier les emplacements de sources de symbole et le comportement de chargement

1. Sélectionnez le **symboles** catégorie sous **outils** (ou **déboguer**) > **Options** > **dedébogage**.

1. Sur le **symboles** page sous **emplacements du fichier (.pdb) de symboles**, sélectionnez **serveurs de symboles Microsoft** aux accès des symboles à partir des serveurs de symboles publics de Microsoft. Sélectionnez les boutons de barre d’outils pour ajouter d’autres emplacements de symboles et de modifier l’ordre de chargement.

1. Pour modifier votre cache de symboles locaux, modifier ou accédez à un autre emplacement sous **mettre en Cache les symboles dans ce répertoire**.

1. Pour télécharger des symboles immédiatement, sélectionnez **charger tous les symboles**. Ce bouton est disponible uniquement pendant le débogage.

   Si vous ne téléchargez les symboles maintenant, vous allez télécharger la prochaine fois que vous démarrez le débogage.

1. Sélectionnez **OK** pour fermer la **Options** boîte de dialogue.

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Pour charger des symboles à partir de Modules ou de la pile des appels windows

1. Pendant le débogage, ouvrez la fenêtre en sélectionnant **déboguer** > **Windows** > **Modules** (ou appuyez sur **Ctrl + Alt + U**) ou **déboguer** > **Windows** > **pile des appels** (**Ctrl + Alt + C**).

1. Cliquez sur un module pour lequel des symboles n’ont pas été chargés. Dans le **Modules** fenêtre, état de chargement des symboles sont dans le **état du symbole** colonne. Dans le **pile des appels** fenêtre, l’état est dans le **état du Frame** colonne et le frame est grisée.

   - Sélectionnez **charger les symboles** dans le menu pour localiser et charger des fichiers de symboles à partir d’un dossier sur votre ordinateur.

   - Sélectionnez **les informations de chargement de symboles** pour afficher les emplacements le débogueur recherche des symboles.

   - Sélectionnez **paramètres des symboles** pour ouvrir le **symboles** page. Sur le **symboles** page sous **emplacements du fichier (.pdb) de symboles**, sélectionnez **serveurs de symboles Microsoft** aux accès des symboles à partir des serveurs de symboles publics de Microsoft. Sélectionnez les boutons de barre d’outils pour ajouter d’autres emplacements de symboles et de modifier l’ordre de chargement. Sélectionnez **OK** pour fermer la boîte de dialogue.

### <a name="see-also"></a>Voir aussi
- [Débogage du code managé](../debugger/debugging-managed-code.md)
- [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)