---
title: Guide pratique pour spécifier le mode d’installation en ligne ou hors connexion ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcd9eeedfdd2a4661e3744da369a6fadc11039a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85381754"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Guide pratique pour spécifier le mode d’installation en ligne et hors connexion ClickOnce
`Install Mode`Pour une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application détermine si l’application sera disponible hors connexion ou en ligne. Lorsque vous choisissez **l’application est disponible en ligne uniquement**, l’utilisateur doit avoir accès à l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] emplacement de publication (une page Web ou un partage de fichiers) pour exécuter l’application. Lorsque vous choisissez **l’application est également disponible hors connexion**, l’application ajoute des entrées au menu **Démarrer** et à la boîte de dialogue **Ajout/suppression de programmes** . l’utilisateur peut exécuter l’application quand elle n’est pas connectée.

`Install Mode`Peut être défini sur la page **publier** du concepteur de **projets**.

> [!NOTE]
> `Install Mode`Peut également être défini à l’aide de l’Assistant Publication. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-make-a-clickonce-application-available-online-only"></a>Pour rendre une application ClickOnce disponible en ligne uniquement

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Dans la zone **mode et paramètres d’installation** , cliquez sur la case d’option **l’application est disponible en ligne uniquement** .

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Pour rendre une application ClickOnce disponible en ligne ou hors connexion

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Dans la zone **mode et paramètres d’installation** , cliquez sur la case d’option **l’application est également disponible hors connexion** .

     Une fois installée, l’application ajoute des entrées au menu **Démarrer** et à **Ajouter ou supprimer des programmes** dans le panneau de configuration.

## <a name="see-also"></a>Voir aussi
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Choisir une stratégie de déploiement ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)