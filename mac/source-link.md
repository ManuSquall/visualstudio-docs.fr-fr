---
title: Débogage dans des packages NuGet avec lien source
description: Cet article décrit la fonctionnalité de liaison de code source dans Visual Studio pour Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451488"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Débogage dans des packages NuGet avec lien source

La technologie de liaison source permet le débogage du code source des assemblys .NET à partir de NuGet fourni par. Fichiers PDB avec liens vers les fichiers sources. Le lien source s’exécute lorsque les développeurs créent leur package NuGet et incorporent les métadonnées de contrôle de code source dans les assemblys et le package. Lorsque le lien source est activé dans Visual Studio pour Mac, l’IDE détecte si les fichiers sources sont disponibles pour les packages installés. Visual Studio pour Mac proposera ensuite de les télécharger, ce qui vous permettra de parcourir le code du package. Le lien source fonctionne également avec le code de bibliothèque de classes de base mono pour les projets Xamarin, ce qui vous permet d’effectuer un pas à pas détaillé dans .NET Framework code. Source Link fournit des métadonnées de contrôle de code source qui améliorent grandement le débogage.

> [!NOTE]
> Visual Studio pour Mac ne prend actuellement pas en charge les serveurs de symboles. Pour cette raison, le lien source avec les métadonnées hébergées sur les serveurs de symboles n’est pas pris en charge.

## <a name="enable-source-link"></a>Activer le lien source

Pour activer le lien source dans Visual Studio pour Mac, accédez à **Visual Studio > préférences... > projets > débogueur** et assurez-vous que la case **pas à pas détaillé du code externe** est cochée.

![Capture d’écran de la boîte de dialogue Préférences montrant le pas à pas détaillé du code externe](media/source-link1.png)

Vous pouvez modifier le paramètre dans **Télécharger le code externe** pour l’adapter à vos préférences :
* Ask : Visual Studio pour Mac vous invite à télécharger le code externe
* Toujours : Visual Studio pour Mac télécharge automatiquement le code externe
* Jamais : Visual Studio pour Mac ne téléchargera pas le code externe associé

Par défaut, l’option **demander** est sélectionnée. L’invite suivante s’affiche lorsque le code externe est trouvé pour un package NuGet :

![Capture d’écran de l’invite qui s’affiche lorsque du code externe est trouvé pour un package NuGet](media/source-link2.png)


## <a name="see-also"></a>Voir aussi

- Le [référentiel github du lien source](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [Documentation .net](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink) sur le lien source et pour plus d’informations sur l’ajout de la prise en charge du lien source aux packages
