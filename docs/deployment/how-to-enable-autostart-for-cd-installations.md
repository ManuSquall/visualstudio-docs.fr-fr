---
title: 'Comment : activer le démarrage automatique pour les Installations de CD | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97642a499e0415dd6fcd245e379c9f01520b5c53
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151244"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Comment : activer le démarrage automatique pour les installations de CD
Lorsque vous déployez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application au moyen de supports amovibles tels que des CD-ROM ou DVD-ROM, vous pouvez activer `AutoStart` afin que le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application est lancée automatiquement lorsque le média est inséré.  
  
 `AutoStart` peut être activé sur le **publier** page de la **Concepteur de projet**.  
  
### <a name="to-enable-autostart"></a>Pour activer le démarrage automatique  
  
1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2.  Cliquez sur le **publier** onglet.  
  
3.  Cliquez sur le **Options** bouton.  
  
     Le **Options de publication** boîte de dialogue s’affiche.  
  
4.  Cliquez sur **déploiement**.  
  
5.  Sélectionnez le **installations pour CD-ROM, démarrer automatiquement l’installation lorsque le CD est inséré** case à cocher.  
  
     Un *Autorun.inf* fichier sera copié à l’emplacement de publication lorsque l’application est publiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)