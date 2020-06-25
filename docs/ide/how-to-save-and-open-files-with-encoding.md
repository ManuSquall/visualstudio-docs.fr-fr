---
title: Guide pratique pour enregistrer et ouvrir des fichiers avec encodage
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Unicode, bidirectional language support
- files, encoding
- bidirectional language support, encoded files
- file encoding, bidirectional languages
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72496e842841b2c55833075e890da4b7088cb489
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284163"
---
# <a name="how-to-save-and-open-files-with-encoding"></a>Guide pratique pour enregistrer et ouvrir des fichiers avec encodage

Vous pouvez enregistrer des fichiers ayant un codage de caractères spécifique pour permettre la prise en charge des langues bidirectionnelles. Vous pouvez également spécifier un codage à l’ouverture d’un fichier, afin que Visual Studio affiche le fichier correctement.

## <a name="to-save-a-file-with-encoding"></a>Pour enregistrer un fichier avec encodage

1. Dans le menu **Fichier**, choisissez **Enregistrer le fichier sous**, puis cliquez sur le bouton déroulant à côté du bouton **Enregistrer**.

     La boîte de dialogue **Options d'enregistrement avancées** est affichée.

2. Sous **Encodage**, sélectionnez l’encodage à utiliser pour le fichier.

3. Éventuellement, sous **Fins de ligne**, sélectionnez le format des caractères de fin de ligne.

     Cette option est utile si vous souhaitez échanger le fichier avec des utilisateurs d’un système d’exploitation différent.

     Si vous souhaitez utiliser un fichier qui est codé de manière spécifique, vous pouvez indiquer à Visual Studio d’utiliser cet encodage à l’ouverture du fichier. La méthode que vous utilisez varie selon que le fichier fait ou non partie de votre projet.

## <a name="to-open-an-encoded-file-that-is-part-of-a-project"></a>Pour ouvrir un fichier encodé qui fait partie d’un projet

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier et choisissez **Ouvrir avec**.

2. Dans la boîte de dialogue **Ouvrir avec**, choisissez l’éditeur avec lequel vous voulez ouvrir le fichier.

     De nombreux éditeurs Visual Studio, tels que l’éditeur de formulaires, détectent automatiquement l’encodage et ouvrent le fichier de façon appropriée. Si vous optez pour un éditeur qui vous permet de choisir l’encodage, la boîte de dialogue **Encodage** s’affiche.

3. Dans la boîte de dialogue **Encodage**, sélectionnez le codage que l’éditeur doit utiliser.

## <a name="to-open-an-encoded-file-that-is-not-part-of-a-project"></a>Pour ouvrir un fichier encodé qui ne fait pas partie d’un projet

1. Dans le menu **Fichier**, pointez sur **Ouvrir**, choisissez **Fichier** ou **Fichier à partir du web**, puis sélectionnez le fichier à ouvrir.

2. Cliquez sur le bouton déroulant en regard du bouton **Ouvrir**, puis choisissez **Ouvrir avec**.

3. Suivez les étapes 2 et 3 de la procédure précédente.

## <a name="see-also"></a>Voir aussi

- [Encodages et sauts de ligne](encodings-and-line-breaks.md)
- [Encodage et globalisation des applications Windows Forms](/dotnet/framework/winforms/advanced/encoding-and-windows-forms-globalization)
- [Globaliser et localiser des applications](../ide/globalizing-and-localizing-applications.md)
