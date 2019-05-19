---
ms.openlocfilehash: 8adac174fbc78778e7154a205088fb9e9a57ae4a
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65846446"
---

1. Sur l’ordinateur sur lequel le projet ASP.NET est ouvert dans Visual Studio, cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions, puis choisissez **Publier**.

1. Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche. Cliquez sur **Créer un profil**.

1. Dans la boîte de dialogue **Choisir une cible de publication**, cliquez sur **Profil d’importation**.

    ![Choisir Publier](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Accédez à l’emplacement du fichier de paramètres de publication que vous avez créé dans la section précédente.

1. Dans la boîte de dialogue **Importer le fichier de paramètres de publication**, accédez au profil que vous avez créé dans la section précédente et sélectionnez-le, puis cliquez sur **Ouvrir**.

    Visual Studio commence le processus de déploiement, tandis que la fenêtre Sortie affiche la progression et les résultats.

    Si vous obtenez des erreurs de déploiement, cliquez sur **Paramètres** pour modifier les paramètres. Modifiez les paramètres, puis cliquez sur **Valider** pour tester les nouveaux paramètres. Si le nom d’hôte est introuvable, essayez de l’adresse IP au lieu du nom d’hôte dans les champs **Serveur** et **URL de destination**.

    ![Modifier les paramètres dans l’outil de publication](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
