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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0187f7dede25900cdf3a78fdbfe2899e5f318472
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043443"
---
# <a name="install-a-uml-profile"></a>Installer un profil UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez étendre Visual Studio avec un profil UML. Un profil vous permet d'ajouter des stéréotypes et des propriétés supplémentaires aux éléments que vous pouvez créer dans des modèles UML. Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Si vous recevez un modèle UML qui a été créé à l'aide de profils, certaines propriétés ne seront pas visibles, à moins que vous n'installiez les mêmes profils.  
  
 Un profil est distribué à l'intérieur d'une Extension Visual Studio. Une extension peut également contenir d'autres fonctionnalités, telles que des commandes de menu. Pour plus d’informations, consultez [la gestion des Extensions Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160728).  
  
### <a name="to-install-a-uml-profile-on-your-computer"></a>Pour installer un profil UML sur votre ordinateur  
  
1. Le profil doit vous avoir été donné sous la forme d'un fichier d'Extension Visual Studio (`.vsix`). Il peut y avoir d'autres fonctionnalités dans le même fichier.  
  
     Déplacez le fichier `.vsix` vers un emplacement approprié sur votre ordinateur.  
  
2. Double-cliquez sur le fichier `.vsix` dans l'Explorateur Windows (ou l'Explorateur de fichiers) ou ouvrez-le dans [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].  
  
3. Cliquez sur **installer** dans la boîte de dialogue qui s’affiche.  
  
4. Pour désinstaller ou temporairement désactiver l’extension, ouvrez **Gestionnaire d’extensions** à partir de la **outils** menu.  
  
### <a name="to-uninstall-or-disable-a-profile-extension"></a>Pour désinstaller ou désactiver une extension de profil  
  
1. Dans Visual Studio **outils** menu, cliquez sur **Gestionnaire d’extensions**.  
  
2. Cliquez sur l’extension que vous souhaitez supprimer, puis cliquez sur **désactiver** ou **désinstallation**.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnaliser votre modèle avec des profils et stéréotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md)
