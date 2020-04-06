---
title: 'Comment : Créer un flux d’atome pour une galerie privée . Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72fbf2d3973ffd84de1cf6f33788c43511c3ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711011"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Comment : Créer un flux Atom pour une galerie privée
Vous pouvez créer un flux Atom (RSS) à un emplacement intranet qui contient des extensions et ajouter le flux à **Extensions et Mises** à jour comme une galerie privée. Pour plus d’informations, consultez [Galeries privées](../extensibility/private-galleries.md).

## <a name="create-an-atom-feed"></a>Créer un flux Atom
 Pour créer un flux Atom comme une galerie privée, vous rassemblez d’abord vos extensions (fichiers *.vsix)* dans un dossier. Vous pouvez les organiser en sous-plis si vous voulez. Vous aurez également besoin des ressources suivantes :

- Un fichier *atom.xml* qui rend les extensions disponibles en galerie privée. Pour plus d’informations sur la façon de connecter le fichier *atom.xml* à **Extensions and Updates**, voir Galeries [privées](../extensibility/private-galleries.md).

- Un dossier qui contient tous les fichiers d’images qui ont été extraits des extensions (par exemple, des captures d’écran). Le fichier *atom.xml* contient des liens relatifs vers ces images afin qu’elles soient disponibles dans **Extensions et Mises à jour**.

  Supposons, par exemple, que vous avez rassemblé les deux extensions suivantes dans un dossier :

- *Template_Wizard_239.vsix*, qui est un modèle de projet VSIX vide.

- *SelectionHighlight.vsix*, qui est un outil pour mettre en évidence tous les cas d’un mot sélectionné.

  Le contenu du fichier *atom.xml* ressemblerait à l’exemple suivant :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<feed xmlns="http://www.w3.org/2005/Atom">
  <title type="text" />
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>
  <updated>2011-04-14T21:25:48Z</updated>
  <entry>
    <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>
    <title type="text">Highlight all occurrences of selected word</title>
    <summary type="text">This extends the editor to highlight ....</summary>
    <published>2011-04-14T14:24:51-07:00</published>
    <updated>2011-04-14T14:24:22-07:00</updated>
    <author>
      <name>Microsoft</name>
    </author>
    <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />
    <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />
    <content type="application/octet-stream" src="SelectionHighlight.vsix" />
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>
      <Version>1.31</Version>
      <References />
      <Rating xsi:nil="true" />
      <RatingCount xsi:nil="true" />
      <DownloadCount xsi:nil="true" />
    </Vsix>
  </entry>
  <entry>
    <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>
    ...
  </entry>
</feed>
```

 Notez que les deux balises de lien se réfèrent à des captures d’écran dans le dossier généré des images.

## <a name="see-also"></a>Voir aussi
- [Galeries privées](../extensibility/private-galleries.md)
