---
title: Concevoir des applications Windows Forms
ms.date: 08/09/2019
ms.topic: overview
helpviewer_keywords:
- Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 03619582a30893c161c44c880a0d9cf6c9766d0b
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768755"
---
# <a name="windows-forms-designer-overview"></a>Vue d’ensemble du Concepteur Windows Forms

Le Concepteur Windows Forms dans Visual Studio fournit une solution de développement rapide pour la création d’applications basées sur Windows Forms. Le Concepteur Windows Forms vous permet d'ajouter facilement des contrôles à un formulaire, de les organiser et d'écrire du code pour leurs événements. Pour plus d’informations sur Windows Forms, consultez [Vue d’ensemble de Windows Forms](/dotnet/framework/winforms/windows-forms-overview).

## <a name="functionality"></a>Fonctionnalité

À l’aide du concepteur, vous pouvez :

- Ajouter des composants, des contrôles de données ou des contrôles Windows à un formulaire.

- Double-cliquez sur le formulaire dans le concepteur et écrivez du code dans l’événement `Load` pour ce formulaire, ou double-cliquez sur un contrôle du formulaire et écrivez du code pour l’événement par défaut du contrôle.

- Modifiez la propriété Text d’un contrôle en sélectionnant le contrôle et en tapant un nom.

- Ajustez le positionnement du contrôle sélectionné en le déplaçant avec la souris ou les touches de direction. De même, ajustez le placement plus précisément à l’aide de Ctrl et des touches fléchées. Enfin, ajustez la taille du contrôle à l’aide de Maj et des touches fléchées.

- Sélectionnez plusieurs contrôles en sélectionnant **Maj** ou **Ctrl** tout en cliquant. Lors de l'utilisation de **Maj**+clic, le premier contrôle sélectionné est le contrôle dominant lors de l’alignement ou de la manipulation de la taille. Lorsque vous utilisez **Ctrl**+clic, le dernier contrôle sélectionné est dominant, donc le contrôle dominant change avec chaque nouveau contrôle ajouté. Vous pouvez également sélectionner plusieurs contrôles en faisant glisser un rectangle de sélection autour des contrôles que vous souhaitez sélectionner.

> [!NOTE]
> Utilisez le Concepteur Windows Forms, et non l’éditeur de ressources, pour apporter des modifications au fichier de ressources d’un formulaire (*.resx*). Si vous modifiez un fichier .resx basé sur des formulaires, vous verrez un avertissement indiquant que les modifications que vous apportez dans l’éditeur de ressources peuvent être perdues. Cela est dû au fait que le Concepteur Windows Forms génère le fichier .resx.

## <a name="see-also"></a>Voir aussi

- [Présentation de Windows Forms](/dotnet/framework/winforms/windows-forms-overview)
- [Contrôles Windows Forms](/dotnet/framework/winforms/controls/)
- [Entrée d’utilisateur dans Windows Forms](/dotnet/framework/winforms/user-input-in-windows-forms)
- [Liaison de données Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding)
- [Améliorer des applications Windows Forms](/dotnet/framework/winforms/advanced/)
- Informations de référence sur l’API <xref:System.Windows.Forms?displayProperty=fullName>
