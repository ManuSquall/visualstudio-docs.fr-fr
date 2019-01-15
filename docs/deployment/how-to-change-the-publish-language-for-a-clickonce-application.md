---
title: 'Procédure : Modifier la langue de publication pour une Application ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21fe434c1128c9f0b81455e010872ccaa49790f2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53871623"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Procédure : Changer la langue de publication d’une application ClickOnce

Lorsque vous publiez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, l’interface utilisateur affichée pendant l’installation par défaut de la langue et la culture de votre ordinateur de développement. Si vous publiez une application localisée, vous devez spécifier une langue et une culture correspondant à la version localisée. Cela est déterminé par le `Publish language` propriété pour votre projet.

Le `Publish language` propriété peut être définie le **Options de publication** boîte de dialogue, accessible à partir de la **publier** page de la **Concepteur de projet**.

> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Pour modifier la langue de publication

1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**.

2.  Cliquez sur l’onglet **Publier**.

3.  Cliquez sur le **Options** bouton pour ouvrir la **Options de publication** boîte de dialogue.

4.  Cliquez sur **Description**.

5.  Dans le **Options de publication** boîte de dialogue zone, sélectionnez une langue et culture à partir de la **langue de publication** liste déroulante, puis cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

- [Publier des applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Guide pratique pour publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)