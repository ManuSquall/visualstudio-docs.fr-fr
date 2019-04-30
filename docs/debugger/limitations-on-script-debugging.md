---
title: Limitations du débogage de Script | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASPX breakpoint mapping, limitations
- script debugging, limitations
- breakpoint mapping, limitations
ms.assetid: 280eead5-693c-47af-967f-dfe9d23f84db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69c5bb23745719edf5e67400d97202f4d14ac17d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846258"
---
# <a name="limitations-on-script-debugging"></a>Limitations du débogage de script
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] prend en charge le débogage de script côté client, sous réserve des limitations de cette rubrique.

## <a name="limitations-on-breakpoint-mapping-with-client-side-script"></a>Limitations relatives au mappage de points d'arrêt avec script côté client
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] vous permet de définir un point d'arrêt dans un fichier ASPX ou HTML côté serveur transformé en fichier côté client au moment de l'exécution. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mappe le point d'arrêt à partir du fichier côté serveur à un point d'arrêt correspondant dans le fichier côté client, selon les limitations suivantes :

- Les points d'arrêt doivent être définis à l'intérieur de blocs `<script>`. Les points d'arrêt dans le script inline ou les blocs `<% %>` ne peuvent pas être mappés.

- L'URL de navigateur pour la page doit contenir le nom de la page. Par exemple, http://microsoft.com/default.apsx. Mappage de point d’arrêt ne peut pas reconnaître une redirection à partir d’une adresse comme http://microsoft.com à la page par défaut.

- Le point d'arrêt doit être défini dans la page spécifiée dans l'URL de navigateur, pas dans un fichier de contrôle ASPX (ascx), une page maître ou un autre fichier inclus dans cette page. Les points d'arrêt définis dans les pages incluses ne peuvent pas être mappés.

- Les points d'arrêt définis dans des blocs `<script defer=true>` ne peuvent pas être mappés.

- Pour les points d'arrêt définis dans des blocs `<script id="">`, le mappage de points d'arrêt ignore l'attribut `id`.

## <a name="breakpoint-mapping-and-duplicate-lines"></a>Mappage de points d'arrêt et doublons
 Pour trouver l'emplacement correspondant dans le script côté serveur et côté client, l'algorithme de mappage de points d'arrêt examine le code sur chaque ligne. L'algorithme suppose que chaque ligne est unique. Si deux ou plusieurs lignes contiennent le même code et si vous définissez un point d'arrêt sur l'un de ces doublons, il se peut que l'algorithme de mappage de points d'arrêt sélectionne le doublon incorrect dans le fichier côté client. Pour empêcher cela, ajoutez un commentaire à la ligne où vous avez défini le point d'arrêt. Exemple :

```csharp
i++ ;
i ++; // I added a comment, so this line is now unique
i ++;
```
