---
title: Modifier la touche d’aide F1
description: Décrit comment remapper ou supprimer le mappage de la touche F1
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
robots: noindex,nofollow
manager: jillfra
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: d9add6996949a97d6140ab6d063f13e02b677e79
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684075"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>Modifier la touche d’aide F1 dans Visual Studio

Si vous souhaitez utiliser la touche F1 pour une fonction différente de celle du service d’aide F1, ou si vous souhaitez simplement désactiver l’aide à l’aide de la touche F1, vous pouvez supprimer ou modifier le mappage de clé.

> [!IMPORTANT]
> Si vous souhaitez désactiver l’aide F1 en raison de problèmes de performances, nous vous recommandons de modifier temporairement le mappage de clé afin de pouvoir tester les améliorations apportées au service d’aide F1 dans mises à jour de Visual Studio. Dans la plupart des scénarios, la touche F1 permet d’ouvrir facilement des pages de référence pour les mots clés de langage et les API à partir de l’éditeur de code, ou d’ouvrir des pages d’aide associées à des éléments Windows ou d’interface utilisateur dans l’IDE. Si vous la désactivez, vous la désactivez pour toutes les utilisations dans Visual Studio.

**Pour désactiver l’aide (F1) :**

1. Dans Visual Studio, sélectionnez **Outils**  >  **options**, puis sous **environnement**, sélectionnez **clavier**.

1. Dans la zone de texte **afficher les commandes contenant** , tapez **help. F1** pour filtrer l’affichage des commandes.

   ![Désactiver l’aide F1](../not-in-toc/media/disable-f1-help-key.png)

1. Sélectionnez **supprimer** pour supprimer le mappage de clé.

1. Sélectionnez la zone de texte **appuyer sur la touche de raccourci** .

1. Sur votre clavier, appuyez sur une nouvelle touche ou combinaison de touches pour l’aide F1 telle que **ALT + F1**, sélectionnez **affecter**, puis sélectionnez **OK**.

Pour plus d’informations sur la définition des raccourcis clavier, consultez [identifier et personnaliser les raccourcis clavier](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
