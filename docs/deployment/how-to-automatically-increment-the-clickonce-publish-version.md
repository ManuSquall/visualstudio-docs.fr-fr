---
title: 'Comment : incrémenter automatiquement la publication ClickOnce Version | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7dd1723d9d92d9bc1b667cc3fddbc3ea297d8b8
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389122"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Guide pratique pour incrémenter automatiquement la version de publication ClickOnce

Lors de la publication une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, en modifiant le `Publish Version` propriété entraîne l’application à publier une mise à jour. Par défaut, Visual Studio incrémente automatiquement le `Revision` numéro de la `Publish Version` chaque fois que vous publiez l’application.

Vous pouvez désactiver ce comportement sur le **publier** page de la **Concepteur de projet**.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Pour désactiver la version de publication à incrémentation automatique

1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2.  Cliquez sur l’onglet **Publier**.

3.  Dans le **Publish Version** section, désactivez le **incrémenter automatiquement la révision avec chaque version** case à cocher.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir la version de publication ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)