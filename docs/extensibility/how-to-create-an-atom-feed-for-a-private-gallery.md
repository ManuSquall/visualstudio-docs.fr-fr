---
title: 'Procédure : Créer un atome de flux pour une galerie privée | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6fc3aef8605f5c3343bcc6aca86513d631cace35
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941688"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Procédure : Créer un flux Atom pour une galerie privée
Vous pouvez créer un flux vers un emplacement intranet qui contient des extensions et ajouter le flux à Atom (RSS) **Extensions et mises à jour** dans une galerie privée. Pour plus d’informations, consultez [galeries privées](../extensibility/private-galleries.md).  
  
## <a name="create-an-atom-feed"></a>Créer un flux Atom  
 Pour créer un flux dans une galerie privée Atom, vous commencez par rassembler vos extensions (*.vsix* fichiers) dans un dossier. Vous pouvez les organiser dans des sous-dossiers si vous le souhaitez. Vous devez également les ressources suivantes :  
  
- Un *atom.xml* fichier qui rend les extensions disponibles dans une galerie privée. Pour plus d’informations sur la connexion le *atom.xml* fichier **Extensions et mises à jour**, consultez [galeries privées](../extensibility/private-galleries.md).  
  
- Un dossier qui contient tous les fichiers image qui ont été extraits à partir des extensions (par exemple, les captures d’écran). Le *atom.xml* fichier contient des liens relatifs à ces images afin qu’ils soient disponibles dans **Extensions et mises à jour**.  
  
  Par exemple, supposons que vous avez collecté les deux extensions suivantes dans un dossier :  
  
- *Template_Wizard_239.vsix*, qui est un modèle de projet VSIX vide.  
  
- *SelectionHighlight.vsix*, qui est un outil pour mettre en surbrillance toutes les instances d’un mot sélectionné.  
  
  Le contenu de la *atom.xml* fichier ressemblerait à l’exemple suivant :  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>   
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
<Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
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
  
 Notez que les balises de deux liens font référence aux captures d’écran dans le dossier généré d’images.  
  
## <a name="see-also"></a>Voir aussi  
 [Galeries privées](../extensibility/private-galleries.md)
