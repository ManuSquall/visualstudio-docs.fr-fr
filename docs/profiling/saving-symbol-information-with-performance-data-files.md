---
title: Enregistrement des informations des symboles avec des fichiers de données de performances | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5a485baaa1fdeab4a0d4c61b82f5381a931ac85
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897184"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Enregistrement des informations des symboles avec des fichiers de données de performances

Si vous utilisez l’IDE de Visual Studio pour analyser les fichiers et que vous envisagez de déplacer votre fichier VSP sur un autre ordinateur, vous devez définir les paramètres du projet de performance de façon à enregistrer ou à *sérialiser* les symboles dans votre fichier de rapport. Ceci augmente la taille d’un fichier de rapport. La sérialisation des symboles est nécessaire pour deux raisons :

- Pour incorporer les symboles de code dans un rapport de performances avant que les assemblys cibles disparaissent de leur emplacement dans le stockage temporaire.

- Pour conserver les symboles, afin que le rapport de performances soit portable depuis l’ordinateur profilé et génère les mêmes informations si le rapport est ouvert pour analyse sur un autre ordinateur, qui peut avoir des symboles différents.

Vous pouvez sérialiser les symboles dans l’IDE de Visual Studio ou en ligne de commande :

- Pour sérialiser les symboles dans l’IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], pointez sur **Outils** dans la barre de menus, puis cliquez sur **Options**. Dans la fenêtre **Options**, sélectionnez **Outils d’analyse des performances**, puis cochez la case **Sérialiser automatiquement les informations de symboles**.

- PACKSYMBOLS est l’option de ligne de commande équivalente quand vous enregistrez des fichiers de rapport. Pour sérialiser les symboles, tapez **vsperfreport /summary:all /packsymbols nom_fichier.vsp**.

## <a name="troubleshooting-symbol-problems"></a>Résolution des problèmes liés aux symboles

Si vous ne voyez aucun symbole dans votre propre code, des solutions courantes sont disponibles :

- Exécutez vsperfreport /debugsympath sur une ligne de commande pour afficher une liste complète des emplacements où les composants du profileur chargent les informations de symboles et si les fichiers de symboles utilisés correspondent aux fichiers utilisés par votre projet.

- Vérifiez que vous exécutez vsperfreport avec l’indicateur /PACKSYMBOLS ou que, dans l’IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], l’option de sérialisation des informations de symboles est sélectionnée dans les options générales de l’Explorateur de performances.

- Si vous avez collecté les données des types, ajoutez /SUMMARY:TYPE à la ligne de commande de vsperfreport.

  Si vous ne voyez pas les symboles de Windows ou d’autres programmes Microsoft :

- Vérifiez que vous avez défini le chemin de votre cache de symboles Windows. Effectuez une des opérations suivantes pour définir le chemin du cache de symboles :

  - Définissez l’option Débogueur->Symboles dans l’IDE [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sur le chemin correct.

  - Ajoutez l’option -symbolpath à la ligne de commande de VSPerfReport pour inclure vos symboles.

- Si vous ne voyez aucun symbole dans [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], vérifiez que vous avez correctement configuré le serveur de symboles pour le serveur ASP.

## <a name="repacking-symbols"></a>Réalisation d’un nouveau pack des symboles

Si vous voulez réaliser un nouveau pack des symboles dans un rapport, vous pouvez le faire à l’aide de l’outil en ligne de commande VsPerfReport. Utilisez les lignes de commande suivantes :

VsPerfReport -clearpackedsymbols nom_fichier.vsp

VsPerfReport -packsymbols -summary:all nom_fichier.vsp

## <a name="see-also"></a>Voir aussi

[Enregistrement et exportation des données des outils d’analyse des performances](../profiling/saving-and-exporting-performance-tools-data.md)  
[Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)  
[VSPerfReport](../profiling/vsperfreport.md)