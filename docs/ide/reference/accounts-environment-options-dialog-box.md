---
title: Informations de référence sur les options de comptes
ms.date: 12/10/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ff457523024db49502ae982a390d9a7be6ba9dd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595902"
---
# <a name="accounts-environment-options-dialog-box"></a>Comptes, Environnement, boîte de dialogue Options

Utilisez cette page pour définir les différentes options relatives aux comptes avec lesquels vous vous connectez à Visual Studio.

## <a name="personalization-account"></a>Compte de personnalisation

### <a name="synchronize-settings-across-devices"></a>Synchroniser les paramètres sur des appareils

Utilisez cette option pour spécifier s’il faut synchroniser vos paramètres sur plusieurs ordinateurs. Pour plus d’informations, consultez [Paramètres synchronisés](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Activer le flux de code de l’appareil

Lorsque cette option est sélectionnée, le comportement de Visual Studio change lorsque vous sélectionnez **Ajouter un compte** dans la page **Fichier** > **Paramètres du compte**. Au lieu de la page **Se connecter à votre compte**, vous voyez une boîte de dialogue contenant une URL et un code à coller dans un navigateur web pour vous connecter. Cette option est utile dans les cas où vous ne pouvez pas vous connecter à Visual Studio de manière classique, par exemple, si vous utilisez une version antérieure d’Internet Explorer, ou si votre pare-feu limite l’accès. Pour plus d'informations, consultez [Work with multiple user accounts](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Clouds Azure inscrits

Cette section montre les instances de cloud Azure auxquelles vous avez accès via un ou plusieurs des comptes que vous utilisez pour vous connecter à Visual Studio. Par exemple, vous avez peut-être accès à une instance privée d’Azure dans le centre de données de votre entreprise. Ou, vous pourriez avoir accès à un cas souverain ou gouvernemental d’Azure comme Azure China 21 Vianet ou Azure U.S. Government. L’instance de cloud Azure globale s’affiche par défaut dans la liste, et vous ne pouvez pas la supprimer.

Inscrivez un cloud Azure supplémentaire en choisissant le bouton **Ajouter**. La boîte de dialogue **Ajouter un nouveau cloud Azure** répertorie plusieurs instances de cloud Azure connues auxquelles vous pouvez vous connecter, ou vous pouvez entrer l’URL d’un point de terminaison Azure privé.

![Ajouter une nouvelle instance de cloud Azure](media/add-new-azure-cloud.png)

Après avoir inscrit un cloud Azure supplémentaire, vous pouvez choisir le cloud Azure auquel vous souhaitez vous connecter lorsque vous ouvrez Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Synchroniser les paramètres sur plusieurs ordinateurs](../synchronized-settings-in-visual-studio.md)
- [Connexion à Visual Studio](../signing-in-to-visual-studio.md)
- [Utiliser plusieurs comptes d’utilisateur](../work-with-multiple-user-accounts.md)
- [Paramètres d'environnement](../environment-settings.md)
