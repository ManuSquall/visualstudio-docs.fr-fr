---
title: Outils de traduction
ms.date: 02/15/2019
ms.topic: reference
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c6934c816574796d59f978c3d2f37f590cf578
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565121"
---
# <a name="develop-globalized-and-localized-apps"></a>Développer des applications mondialisées et traduites

Visual Studio facilite le développement à destination d’un public international en tirant parti des services intégrés dans [.NET](/dotnet/standard/globalization-localization/).

Par exemple, le système de projet pour les applications Windows Forms peut générer des fichiers de ressources pour la culture d’interface utilisateur de secours et chaque culture d’interface utilisateur supplémentaire. Quand vous générez un projet dans Visual Studio, les fichiers de ressources sont compilés à partir du format XML de Visual Studio (.resx) vers un format binaire intermédiaire (.resources), puis incorporés dans des assemblys satellites. Pour plus d’informations, consultez [Fichiers de ressources dans Visual Studio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) et [Créer des assemblys satellites pour des applications de bureau](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps).

## <a name="bidirectional-languages"></a>Langues bidirectionnelles

Vous pouvez utiliser Visual Studio pour créer des applications qui affichent correctement les langues qui s’écrivent de droite à gauche, comme l’arabe et l’hébreu. Pour certaines fonctionnalités, il suffit de définir des propriétés. Dans d’autres cas, vous devez implémenter des fonctionnalités dans le code.

> [!NOTE]
> Pour entrer et afficher des langues bidirectionnelles, vous devez utiliser une version de Windows configurée avec la langue appropriée. Il peut s’agir d’une version anglaise de Windows sur laquelle est installé le module linguistique correspondant, ou d’une version localisée de Windows.

### <a name="apps-that-support-bidirectional-languages"></a>Applications prenant en charge les langues bidirectionnelles

- Applications Windows

   Vous pouvez créer des applications entièrement bidirectionnelles prenant en charge le texte bidirectionnel, l’ordre de lecture de droite à gauche et la mise en miroir (c’est-à-dire l’inversion de la disposition des fenêtres, des menus, des boîtes de dialogue, etc.). À l’exception de la mise en miroir, ces fonctionnalités sont disponibles par défaut ou en tant que paramètres de propriété. La mise en miroir est prise en charge par défaut pour certaines fonctionnalités, telles que les boîtes de message. Dans d’autres cas, vous devez implémenter la mise en miroir dans votre code. Pour plus d’informations, consultez la page sur la [prise en charge bidirectionnelle des applications Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

- Applications web

   Les services web prennent en charge l’envoi et la réception de texte UTF-8 et Unicode. Ils sont donc adaptés aux applications qui comportent des langues bidirectionnelles. Les applications clientes web s’appuient sur les navigateurs pour leur interface utilisateur. Le degré de prise en charge des fonctionnalités bidirectionnelles d’une application web dépend donc de celui du navigateur de l’utilisateur. Dans Visual Studio, vous pouvez créer des applications avec prise en charge de l’arabe ou de l’hébreu, de l’ordre de lecture de droite à gauche, de l’encodage des fichiers et des paramètres de culture locale. Pour plus d’informations, consultez la page [Prise en charge bidirectionnelle pour les applications web ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

> [!NOTE]
> Les applications console ne prennent pas en charge le texte des langues bidirectionnelles. Cela est dû à la façon dont Windows fonctionne avec les applications console.

## <a name="see-also"></a>Voir aussi

- [Prise en charge des langues bidirectionnelles dans Visual Studio](use-bidirectional-languages.md)
- [Internationaliser et traduire des applications .NET](/dotnet/standard/globalization-localization/)
- [Ressources dans les applications .NET](/dotnet/framework/resources/)
