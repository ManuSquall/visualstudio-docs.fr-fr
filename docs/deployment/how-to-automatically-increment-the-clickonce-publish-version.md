---
title: Incrémenter automatiquement la version de publication ClickOnce
description: Découvrez comment désactiver l’incrémentation automatique du numéro de révision de votre application ClickOnce à l’aide de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4d39654134177f3936bd2fbe72b6786ca9cf03c
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382622"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Guide pratique pour incrémenter automatiquement la version de publication ClickOnce

Lors de la publication d’une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, la modification de la `Publish Version` propriété entraîne la publication de l’application en tant que mise à jour. Par défaut, Visual Studio incrémente automatiquement le `Revision` numéro de `Publish Version` chaque fois que vous publiez l’application.

Vous pouvez désactiver ce comportement sur la page **publier** du **Concepteur de projets**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Pour désactiver l’incrémentation automatique de la version de publication

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions** , dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Dans la section **version de publication** , désactivez la case à cocher **incrémenter automatiquement la révision avec chaque version** .

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir la version de publication ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)