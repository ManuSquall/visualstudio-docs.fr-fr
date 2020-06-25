---
title: Comment déboguer la source de .NET Framework | Microsoft Docs
ms.date: 11/19/2018
ms.topic: how-to
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3f043aae44231608fb514e87a05717f4aeb924bc
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350093"
---
# <a name="how-to-debug-net-framework-source"></a>Guide pratique pour déboguer une source .NET Framework

Pour déboguer .NET Framework source, vous devez :

- Permet d’effectuer un pas à pas détaillé dans la source de .NET Framework.

- Avoir accès aux symboles de débogage pour le code.

  Vous pouvez choisir de télécharger immédiatement les symboles de débogage ou de définir des options pour les télécharger ultérieurement. Si vous ne téléchargez pas les symboles immédiatement, ils seront téléchargés la prochaine fois que vous démarrerez le débogage de votre application. Lors du débogage, vous pouvez également utiliser les fenêtres **modules** ou **pile des appels** pour télécharger et charger des symboles.

### <a name="to-enable-stepping-into-net-framework-source"></a>Pour activer le pas à pas détaillé dans la source de .NET Framework

1. Sous **Outils** (ou **débogage**) > **options**  >  **débogage**  >  **général**, sélectionnez **activer l’exécution pas à pas .NET Framework source**.

   - Si l'option Uniquement mon code était activée, une boîte de dialogue d'avertissement s'affiche pour signaler que cette option est à présent désactivée. Sélectionnez **OK**.

   - Si vous n’avez pas défini de cache de symboles local, une boîte de dialogue d’avertissement vous indique qu’un cache de symboles par défaut a été défini. Sélectionnez **OK**.

1. Sélectionnez **OK** pour fermer la boîte de dialogue **options** .

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Pour définir ou modifier les emplacements des sources de symboles et le comportement de chargement

1. Sélectionnez la catégorie **symboles** sous **Outils** (ou **débogage**) > **options**de  >  **débogage**.

1. Dans la page **symboles** , sous **emplacements du fichier de symboles (. pdb)**, sélectionnez **serveurs de symboles Microsoft** pour accéder aux symboles à partir des serveurs de symboles publics Microsoft. Sélectionnez les boutons de la barre d’outils pour ajouter d’autres emplacements de symboles et modifier l’ordre de chargement.

1. Pour modifier votre cache de symboles local, modifiez ou accédez à un autre emplacement sous les **symboles du cache dans ce répertoire**.

1. Pour télécharger des symboles immédiatement, sélectionnez **charger tous les symboles**. Ce bouton est disponible uniquement pendant le débogage.

   Si vous ne téléchargez pas les symboles maintenant, ils seront téléchargés la prochaine fois que vous démarrerez le débogage.

1. Sélectionnez **OK** pour fermer la boîte de dialogue **options** .

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Pour charger des symboles à partir des fenêtres modules ou pile des appels

1. Pendant le débogage, ouvrez la fenêtre en sélectionnant **Déboguer**les  >  **Windows**  >  **modules** Windows (ou appuyez sur **Ctrl + Alt + U**) ou **Déboguer**la pile des  >  **Windows**  >  **appels** Windows (**Ctrl + Alt + C**).

1. Cliquez avec le bouton droit sur un module pour lequel les symboles n’ont pas été chargés. Dans la fenêtre **modules** , l’état du chargement des symboles se trouve dans la colonne **État des symboles** . Dans la fenêtre **pile des appels** , l’État est dans la colonne État du **Frame** et le cadre est grisé.

   - Sélectionnez **charger les symboles** dans le menu pour rechercher et charger les fichiers de symboles à partir d’un dossier sur votre ordinateur.

   - Sélectionnez **informations** sur le chargement de symboles pour afficher les emplacements où le débogueur a effectué une recherche de symboles.

   - Sélectionnez **paramètres des symboles** pour ouvrir la page **symboles** . Dans la page **symboles** , sous **emplacements du fichier de symboles (. pdb)**, sélectionnez **serveurs de symboles Microsoft** pour accéder aux symboles à partir des serveurs de symboles publics Microsoft. Sélectionnez les boutons de la barre d’outils pour ajouter d’autres emplacements de symboles et modifier l’ordre de chargement. Sélectionnez **OK** pour fermer la boîte de dialogue.

### <a name="see-also"></a>Voir aussi
- [Débogage de code managé](../debugger/debugging-managed-code.md)
- [Spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)