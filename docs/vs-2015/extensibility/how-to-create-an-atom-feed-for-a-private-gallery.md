---
title: 'Comment : créer un flux Atom pour une galerie privée | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6d4ba78028774e8fbf8e281afa2855781dab43a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204212"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Guide pratique pour créer un flux Atom pour une galerie privée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez créer un flux Atom (RSS) à un emplacement intranet qui contient des extensions et ajouter le flux aux **extensions et aux mises à jour** en tant que galerie privée. Pour plus d’informations, consultez [galeries privées](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Création d’un flux Atom  
 Pour créer un flux Atom en tant que galerie privée, vous devez d’abord regrouper vos extensions (fichiers. VSIX) dans un dossier. Si vous le souhaitez, vous pouvez les organiser dans des sous-dossiers. Vous aurez également besoin des ressources suivantes :  
  
- Fichier atom.xml qui rend les extensions disponibles en tant que galerie privée. Pour plus d’informations sur la façon de connecter le fichier atom.xml aux **extensions et aux mises à jour**, consultez [galeries privées](../extensibility/private-galleries.md).  
  
- Dossier qui contient tous les fichiers image qui ont été extraits des extensions (par exemple, les captures d’écran). Le fichier atom.xml contient des liens relatifs vers ces images afin qu’elles soient disponibles dans **extensions et mises à jour**.  
  
  Par exemple, supposons que vous avez rassemblé les deux extensions suivantes dans un dossier :  
  
- Template_Wizard_239. vsix, qui est un modèle de projet VSIX vide.  
  
- SelectionHighlight. vsix, outil qui permet de mettre en surbrillance toutes les instances d’un mot sélectionné.  
  
  Le contenu du fichier atom.xml ressemble à l’exemple suivant :  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ….</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  …  
  </entry>  
  </feed>  
  
```  
  
 Notez que les deux balises de lien font référence à des captures d’écran dans le dossier d’images généré.  
  
## <a name="see-also"></a>Voir aussi  
 [Galeries privées](../extensibility/private-galleries.md)
