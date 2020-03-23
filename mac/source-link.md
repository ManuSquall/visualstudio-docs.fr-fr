---
title: Débogage dans les paquets NuGet avec Source Link
description: Cet article décrit la fonction Source Link dans Visual Studio for Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/16/2019
ms.assetid: 4bcb8acf-db50-4bd8-a48e-86248f00c90b
ms.openlocfilehash: 530ad09bbf72d9696621f328c2df40b37f362c13
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451488"
---
# <a name="debugging-into-nuget-packages-with-source-link"></a>Débogage dans les paquets NuGet avec Source Link

La technologie Source Link permet le débogage de code source des assemblages .NET de NuGet ce navire . PDB avec des liens vers des fichiers source. Source Link s’exécute lorsque les développeurs créent leur paquet NuGet et intègrent des métadonnées de contrôle source à l’intérieur des assemblages et du paquet. Lorsque Source Link est activé dans Visual Studio pour Mac, l’IDE détecte si des fichiers sources sont disponibles pour les paquets installés. Visual Studio pour Mac vous proposera ensuite de les télécharger, ce qui vous permettra de passer à travers le code du paquet. Source Link fonctionne également avec le code Mono Base Class Library pour les projets Xamarin, vous permettant d’entrer dans le code cadre .NET ainsi. Source Link fournit des métadonnées de contrôle de code source qui améliorent grandement le débogage.

> [!NOTE]
> Visual Studio pour Mac ne prend pas actuellement en charge les serveurs de symboles. Pour cette raison, Source Link avec des métadonnées hébergées sur les serveurs de symboles n’est pas pris en charge.

## <a name="enable-source-link"></a>Activer le lien source

Pour activer Source Link en Visual Studio pour Mac, naviguez vers **Visual Studio > Préférences... > Projects > Debugger** et assurez-vous que **l’étape dans** la case à cocher de code externe est vérifiée.

![Capture d’écran des préférences dialogue montrant Step dans la case à cocher de code externe](media/source-link1.png)

Vous pouvez modifier le paramètre dans Télécharger le **code externe** en fonction de vos préférences :
* Demandez: Visual Studio pour Mac vous incitera à télécharger le code externe
* Toujours: Visual Studio pour Mac téléchargera le code externe automatiquement
* Jamais : Visual Studio pour Mac ne téléchargera pas le code externe connexe

Par défaut, **Ask** est sélectionné. Vous recevrez l’invite suivante lorsque le code externe est trouvé pour un paquet NuGet :

![Capture d’écran de l’invite qui apparaît lorsque le code externe est trouvé pour un paquet NuGet](media/source-link2.png)


## <a name="see-also"></a>Voir aussi

- Le [référentiel Source Link GitHub](https://github.com/dotnet/sourcelink/blob/master/README.md)
- [.NET documentation](https://docs.microsoft.com/dotnet/standard/library-guidance/sourcelink) sur Source Link et pour plus d’informations sur la façon d’ajouter le support Source Link aux paquets
