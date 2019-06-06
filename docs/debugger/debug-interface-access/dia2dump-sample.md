---
title: Exemple de Dia2dump | Microsoft Docs
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c8b92ae2f607ae449b7b4392fc3638fcdcb6a80
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715345"
---
# <a name="dia2dump-sample"></a>Dia2dump, exemple

L’exemple Dia2dump montre comment utiliser le Microsoft Debug Interface Access Kit de développement logiciel (DIA SDK) pour interroger un fichier PDB pour plus d’informations.

L’exemple Dia2dump est installé avec Visual Studio et contient les fichiers solution et la source. Le fichier exécutable compilé s’exécute à partir de la ligne de commande. Il peut afficher le contenu d’un fichier de base de données (.pdb) programme entier ou simplement les sections qui vous intéressent.

## <a name="install-the-sample"></a>Installer l’exemple

L’exemple est installé lorsque vous choisissez la **développement Desktop en C++** charge de travail dans Visual Studio Installer. Pour plus d’informations sur la façon d’installer Visual Studio et choisissez les charges de travail spécifiques et des composants individuels, consultez [installer Visual Studio](../../install/install-visual-studio.md).

Lors de l’installation, l’exemple est dans votre répertoire d’installation de Visual Studio, dans un sous-répertoire nommé \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Générer l’exemple

Par défaut, le répertoire d’installation est un répertoire protégé. Cela signifie que vous devez utiliser une invite de commandes avec élévation de privilèges développeur ou une instance de Visual Studio pour créer et modifier l’exemple de solution à cet emplacement. Pour simplifier la génération, nous vous recommandons tout d’abord copiez les fichiers à partir du répertoire d’exemple vers un autre répertoire, tel qu’un dossier dans votre dossier Documents et puis générez l’exemple.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Pour générer l’exemple Dia2Dump dans Visual Studio

1. Ouvrez le fichier DIA2Dump.sln dans Visual Studio. Si vous n’avez pas copié la solution vers un autre répertoire, vous pouvez être invité à redémarrer Visual Studio avec des autorisations élevées.

1. Dans **l’Explorateur de solutions**, sélectionnez le projet Dia2Dump (pas la solution).

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](/cpp/build/working-with-project-properties).

1. Ouvrez le **propriétés de Configuration** > **C/C++**  > **général** page de propriétés.

1. Dans le **autres répertoires Include** propriété, choisissez le contrôle de liste déroulante, puis choisissez **modifier**.

1. Dans le **autres répertoires Include** boîte de dialogue, dans le champ d’édition, entrez le `$(VSInstallDir)DIA SDK\include` directory. Ajouter ce répertoire pour garantir que le compilateur peut trouver le fichier dia2.h. Choisissez **OK** pour enregistrer vos modifications.

1. Choisissez **OK** pour enregistrer vos modifications dans les propriétés du projet.

1. Sur le **Build** menu, choisissez **régénérer la Solution**. Par défaut, Visual Studio génère une version Debug de l’exemple, situé dans un sous-répertoire de débogage du répertoire de solution.

1. Fermez Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Pour générer l’exemple Dia2Dump en ligne de commande

1. Dans une fenêtre d’invite de commandes développeur, accédez au répertoire où vous avez copié les fichiers d’exemple. Si vous n’avez pas copier l’exemple vers un autre répertoire, vous devez utiliser avec une élévation de privilèges (exécuter en tant qu’administrateur) fenêtre d’invite de commandes développeur.

1. Entrez la commande `nmake makefile` pour élaborer la configuration de débogage par défaut de dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Exécuter l’exemple Dia2Dump

Dia2Dump.exe s’appuie sur le msdia*version*server .dll COM de fournir ses services. À partir de Visual Studio 2015, la version est msdia140.dll. Si le msdia*version*.dll COM serveur n’est pas initialisé, vous devez l’enregistrer dia2dump.exe peut fonctionner. Le répertoire de DIA SDK contient un sous-répertoire bin qui contient le x86 version de la DLL. Une version pour x64 machines de l’architecture est dans bin\amd64, et une version pour ARM est dans bin\arm. Pour inscrire la dll, ouvrez une fenêtre d’invite de commandes développeur avec élévation de privilèges et accédez au répertoire qui contient la version de votre architecture de l’ordinateur. Entrez la commande `regsvr32 msdia140.dll` pour inscrire le serveur COM.

### <a name="to-run-the-sample"></a>Pour exécuter l'exemple

1. Ouvrez une invite de commandes et accédez au répertoire qui contient le dia2dump.exe que vous avez créée.

1. Entrez la commande `dia2dump filename` où *filename* est le nom d’un fichier PDB à examiner. Si le fichier PDB est dans un autre répertoire, utilisez le chemin d’accès complet au fichier en tant que *filename*. Cette commande répertorie toutes les données dans le fichier PDB.

1. Dia2Dump a d’autres options pour afficher uniquement les informations sélectionnées. Utilisez le `dia2dump -?` commande pour répertorier toutes les options disponibles.

## <a name="see-also"></a>Voir aussi

- [Porter, migrer et mettre à niveau des projets Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
