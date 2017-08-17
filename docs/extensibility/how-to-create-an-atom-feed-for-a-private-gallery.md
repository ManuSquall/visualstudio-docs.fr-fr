---
title: "Comment : créer un Atom pour une galerie privée d’alimentation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 62714327dfc3ebc84d624c21c8ff63bdb5bc440c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/17/2017

---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Comment : créer un Atom pour une galerie privée d’alimentation
Vous pouvez créer un flux à un emplacement intranet qui contient des extensions et ajouter des flux à Atom (RSS) **Extensions et mises à jour** dans une galerie privée. Pour plus d’informations, consultez [galeries privées](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Création d’un Atom flux  
 Pour créer un flux dans une galerie privée Atom, vous rassembler vos extensions (fichiers .vsix) dans un dossier. Vous pouvez les organiser dans des sous-dossiers si vous le souhaitez. Vous devez également les ressources suivantes :  
  
-   Un fichier atom.xml qui rend les extensions disponibles dans une galerie privée. Pour plus d’informations sur la façon de connecter le fichier atom.xml à **Extensions et mises à jour**, consultez [galeries privées](../extensibility/private-galleries.md).  
  
-   Un dossier qui contienne les fichiers d’image qui ont été extraits par les extensions (par exemple, les captures d’écran). Le fichier atom.xml contient des liens relatifs à ces images afin qu’ils soient disponibles dans **Extensions et mises à jour**.  
  
 Par exemple, supposons que vous avez rassemblé les deux extensions suivantes dans un dossier :  
  
-   Template_Wizard_239.VSIX, qui est un modèle de projet VSIX vide.  
  
-   SelectionHighlight.vsix, qui est un outil pour mettre en surbrillance toutes les instances d’un mot sélectionné.  
  
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
  <summary type="text">This extends the editor to highlight ....</summary>   
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
  ...  
  </entry>  
  </feed>  
  
```  
  
 Notez que les deux balises de liens font référence à des captures d’écran dans le dossier généré d’images.  
  
## <a name="see-also"></a>Voir aussi  
 [Galeries privées](../extensibility/private-galleries.md)
