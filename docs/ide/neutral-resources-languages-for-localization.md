---
title: Langues des ressources neutres pour la localisation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1a671eefae23fb369cd7398efb7589764ebb46f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55912870"
---
# <a name="neutral-resources-languages-for-localization"></a>Langues des ressources neutres pour la localisation

La classe <xref:System.Resources.NeutralResourcesLanguageAttribute> spécifie la culture des ressources incluses dans l’assembly principal. Cet attribut est utilisé comme une amélioration des performances, afin que l’objet <xref:System.Resources.ResourceManager> ne recherche pas des ressources qui sont incluses dans l’assembly principal.

 Le code suivant illustre la définition du langage des ressources neutre. Le code peut être placé dans un script de build, ou dans le fichier AssemblyInfo.vb ou AssemblyInfo.cs.

```vb
' Set neutral resources language for assembly.
<Assembly: NeutralResourcesLanguageAttribute("en")>
```

```csharp
// Set neutral resources language for assembly.
[assembly: NeutralResourcesLanguageAttribute("en")]
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Resources.ResourceManager>
- [Introduction aux applications internationales basées sur le .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [Organisation hiérarchique des ressources pour la localisation](../ide/hierarchical-organization-of-resources-for-localization.md)
- [Localisation d’applications](../ide/localizing-applications.md)
- [Globalisation et localisation d’applications](../ide/globalizing-and-localizing-applications.md)