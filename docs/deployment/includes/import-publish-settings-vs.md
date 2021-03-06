---
ms.openlocfilehash: 94c2c733b631ef5e727c79a6e093bb224aec38c4
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249854"
---

1. Sur l’ordinateur sur lequel le projet ASP.NET est ouvert dans Visual Studio, cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions, puis choisissez **Publier**.

   Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche. Cliquez sur **nouveau** ou sur **créer un profil**.

1. Sélectionnez l’option permettant d’importer un profil.

   ::: moniker range=">=vs-2019"
   Dans la boîte de dialogue **publier** , cliquez sur **Importer un profil**.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Dans la boîte de dialogue **Choisir une cible de publication**, cliquez sur **Profil d’importation**.
   ::: moniker-end

   ![Choisir Publier](../../deployment/media/tutorial-publish-tool-import-profile.png)

1. Accédez à l’emplacement du fichier de paramètres de publication que vous avez créé dans la section précédente.

1. Dans la boîte de dialogue **importer le fichier de paramètres de publication** , accédez à et sélectionnez le profil que vous avez créé dans la section précédente, puis cliquez sur **ouvrir**.

   ::: moniker range=">=vs-2019"
   Cliquez sur **Terminer** pour enregistrer le profil de publication, puis cliquez sur **publier**.

   Visual Studio commence le processus de déploiement, tandis que la fenêtre Sortie affiche la progression et les résultats.

   Si vous recevez des erreurs de déploiement, cliquez sur **modifier** pour modifier les paramètres. Modifiez les paramètres, puis cliquez sur **Valider** pour tester les nouveaux paramètres. Si le nom d’hôte est introuvable, essayez de l’adresse IP au lieu du nom d’hôte dans les champs **Serveur** et **URL de destination**.
   ::: moniker-end
   ::: moniker range="vs-2017"
   Visual Studio commence le processus de déploiement, tandis que la fenêtre Sortie affiche la progression et les résultats.

   Si vous obtenez des erreurs de déploiement, cliquez sur **Paramètres** pour modifier les paramètres. Modifiez les paramètres, puis cliquez sur **Valider** pour tester les nouveaux paramètres. Si le nom d’hôte est introuvable, essayez de l’adresse IP au lieu du nom d’hôte dans les champs **Serveur** et **URL de destination**.
   ::: moniker-end

   ![Modifier les paramètres dans l’outil de publication](../../deployment/media/tutorial-configure-publish-settings-in-tool.png)
