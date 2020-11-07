---
title: Spécifier l’emplacement à partir duquel les utilisateurs finaux s’installent
description: Découvrez comment définir la propriété URL d’installation, où une application ClickOnce publiée est hébergée pour l’installation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3518a2eef331414e5c73c0cebb36681ad2b72d61
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349618"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Guide pratique pour spécifier l’emplacement à partir duquel les utilisateurs finaux effectueront l’installation

Lors de la publication d’une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application, l’emplacement où les utilisateurs accèdent au téléchargement et à l’installation de l’application n’est pas nécessairement l’emplacement où vous publiez initialement l’application. Par exemple, dans certaines organisations, un développeur peut publier une application sur un serveur intermédiaire, puis un administrateur déplace l’application vers un serveur Web.

Dans ce cas, vous pouvez utiliser la `Installation URL` propriété pour spécifier le serveur Web sur lequel les utilisateurs doivent accéder pour télécharger l’application. Cela est nécessaire pour que le manifeste d’application sache où rechercher les mises à jour.

La `Installation URL` propriété peut être définie sur la page **publier** du **Concepteur de projets**.

> [!NOTE]
> La `Installation URL` propriété peut également être définie à l’aide de **Assistant Publication**. Pour plus d’informations, consultez [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Pour spécifier une URL d’installation

1. Après avoir sélectionné un projet dans l’ **Explorateur de solutions** , dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l'onglet **Publier**.

3. Dans le champ URL d’installation, entrez l’emplacement d’installation à l’aide d’une URL complète au format `https://www.contoso.com/ApplicationName` , ou un chemin d’accès UNC utilisant le format `\Server\ApplicationName` .

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour spécifier l’endroit où Visual Studio copie les fichiers](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Publication d’applications ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Comment : publier une application ClickOnce à l’aide de l’Assistant Publication](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)