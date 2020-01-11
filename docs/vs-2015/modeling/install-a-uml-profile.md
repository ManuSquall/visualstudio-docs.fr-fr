---
title: Installer un profil UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, profiles
ms.assetid: 586f9ba5-4d01-4a1d-b001-32e2efaa4f24
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89531fe0f2e912a6aabd962ab56ca7a24a7f3e20
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850662"
---
# <a name="install-a-uml-profile"></a>Installer un profil UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez étendre Visual Studio avec un profil UML. Un profil vous permet d'ajouter des stéréotypes et des propriétés supplémentaires aux éléments que vous pouvez créer dans des modèles UML. Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Si vous recevez un modèle UML qui a été créé à l'aide de profils, certaines propriétés ne seront pas visibles, à moins que vous n'installiez les mêmes profils.

 Un profil est distribué à l'intérieur d'une Extension Visual Studio. Une extension peut également contenir d'autres fonctionnalités, telles que des commandes de menu. Pour plus d’informations, consultez [gestion des extensions Visual Studio](https://msdn.microsoft.com/library/dd293638(VS.100).aspx).

### <a name="to-install-a-uml-profile-on-your-computer"></a>Pour installer un profil UML sur votre ordinateur

1. Le profil doit vous avoir été donné sous la forme d'un fichier d'Extension Visual Studio (`.vsix`). Il peut y avoir d'autres fonctionnalités dans le même fichier.

     Déplacez le fichier `.vsix` vers un emplacement approprié sur votre ordinateur.

2. Double-cliquez sur le fichier `.vsix` dans l'Explorateur Windows (ou l'Explorateur de fichiers) ou ouvrez-le dans [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

3. Cliquez sur **installer** dans la boîte de dialogue qui s’affiche.

4. Pour désinstaller ou désactiver temporairement l’extension, ouvrez le **Gestionnaire d’extensions** à partir du menu **Outils** .

### <a name="to-uninstall-or-disable-a-profile-extension"></a>Pour désinstaller ou désactiver une extension de profil

1. Dans le menu **Outils** de Visual Studio, cliquez sur **Gestionnaire d’extensions**.

2. Cliquez sur l’extension que vous souhaitez supprimer, puis sur **Désactiver** ou **désinstaller**.

## <a name="see-also"></a>Voir aussi
 [Personnaliser votre modèle avec des profils et des stéréotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md)
