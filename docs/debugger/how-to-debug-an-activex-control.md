---
title: 'Comment : déboguer un contrôle ActiveX | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75abf76516d3827a748e1b896d4c2e8c93bb34da
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733868"
---
# <a name="how-to-debug-an-activex-control"></a>Comment : déboguer un contrôle ActiveX

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez Importation et exportation de paramètres dans le menu Outils. Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

Pour déboguer votre contrôle ActiveX, vous devez spécifier un conteneur (exécutable) à utiliser pour l'exécution du contrôle.

## <a name="to-specify-a-container-for-the-debug-session"></a>Pour spécifier un conteneur pour une session de débogage

1. Dans l'Explorateur de solutions, sélectionnez le projet.

2. Dans le menu **affichage** , cliquez sur **pages de propriétés**.

3. Dans la boîte de dialogue **Pages de propriété de projet**, ouvrez le dossier **Propriétés de configuration** et sélectionnez **Débogage**.

4. Dans la catégorie **Débogage**, recherchez la propriété **Commande**.

5. Spécifiez le nom de chemin pour le conteneur. Par exemple, C:\Program Files\Internet Explorer\IEXPLORE.EXE.

6. Si vous spécifiez Internet Explorer comme conteneur et que vous utilisez Active Desktop, tapez `/new` dans la zone **Arguments de la commande**.

7. Cliquez sur **OK**.

     Si vous ne spécifiez pas un conteneur dans la boîte de dialogue **Pages de propriétés de projet**, vous pouvez spécifier le conteneur quand vous commencez à déboguer. Quand vous sélectionnez une commande d’exécution pour commencer le débogage, la [boîte de dialogue Exécutable pour la session de débogage](../debugger/executable-for-debugging-session-dialog-box.md) s’affiche. Spécifiez le nom de chemin du conteneur dans la boîte de dialogue.

## <a name="see-also"></a>Voir aussi

- [Contrôles ActiveX](/cpp/mfc/activex-controls)
- [Test des propriétés et des événements avec le conteneur de test](/cpp/mfc/testing-properties-and-events-with-test-container)
- [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)
- [Débogage dans Visual Studio](../debugger/index.yml)
- [Présentation du débogueur](../debugger/debugger-feature-tour.md)