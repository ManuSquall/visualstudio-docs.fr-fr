---
title: 'Comment : créer un atome de flux pour une galerie privée | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c6d46129a77d0d6e0b764f2921dce77014b865f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516590"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Comment : créer un atome de flux pour une galerie privée
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : créer un flux Atom pour une galerie privée](https://docs.microsoft.com/visualstudio/extensibility/how-to-create-an-atom-feed-for-a-private-gallery).  
  
Vous pouvez créer un flux vers un emplacement intranet qui contient des extensions et ajouter le flux à Atom (RSS) **Extensions et mises à jour** dans une galerie privée. Pour plus d’informations, consultez [Galeries privées](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Création d’un atome de flux  
 Pour créer un flux dans une galerie privée Atom, vous commenciez par vos extensions (fichiers .vsix) dans un dossier. Vous pouvez les organiser dans des sous-dossiers si vous le souhaitez. Vous devez également les ressources suivantes :  
  
-   Un fichier atom.xml qui rend les extensions disponibles dans une galerie privée. Pour plus d’informations sur la façon de connecter le fichier atom.xml à **Extensions et mises à jour**, consultez [galeries privées](../extensibility/private-galleries.md).  
  
-   Un dossier qui contient tous les fichiers image qui ont été extraits à partir des extensions (par exemple, les captures d’écran). Le fichier atom.xml contient des liens relatifs à ces images afin qu’ils soient disponibles dans **Extensions et mises à jour**.  
  
 Par exemple, supposons que vous avez collecté les deux extensions suivantes dans un dossier :  
  
-   Template_Wizard_239.VSIX, qui est un modèle de projet VSIX vide.  
  
-   SelectionHighlight.vsix, qui est un outil pour mettre en surbrillance toutes les instances d’un mot sélectionné.  
  
 Le contenu du fichier atom.xml ressemblerait à l’exemple suivant :  
  
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
  
 Notez que les balises de deux liens font référence aux captures d’écran dans le dossier généré d’images.  
  
## <a name="see-also"></a>Voir aussi  
 [Galeries privées](../extensibility/private-galleries.md)

