---
title: schémas XML
description: En savoir plus sur la boîte de dialogue schémas XML qui permet de sélectionner le (s) schéma (s) de langage XSD (XML Schema Definition) à associer à un document XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1c91e97d0508ab85893409386ddd3ab9dded7f45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874832"
---
# <a name="xml-schemas-dialog-box"></a>Boîte de dialogue Schémas XML

La boîte de dialogue **schémas XML** permet de sélectionner le (s) schéma (s) de langage XSD (XML Schema Definition) à associer à un document XML. Vous pouvez sélectionner un schéma dans le cache de schéma ou spécifier un schéma situé ailleurs dans le cache. Les schémas sélectionnés sont considérés comme faisant partie d'un jeu de schémas. Le jeu de schémas est utilisé pour IntelliSense et pour la validation de documents XML.

Pour accéder à la boîte de dialogue **schémas XML** , vous pouvez soit cliquer sur le bouton **schémas** de la fenêtre Propriétés du document, soit sélectionner **schémas** dans le menu **XML** .

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

**Utilisation**

Sélectionnez la manière dont le schéma XML doit être utilisé.

- **Automatique**. Ce schéma n'est pas utilisé par le document en cours mais est disponible pour l'association automatique. Si le document XML déclare un espace de noms qui correspond au `targetNamespace` de ce schéma, le schéma sera automatiquement associé et inclus dans le jeu de schémas.

- **Utilisez ce schéma**. Ce schéma est utilisé par le document en cours. Soit l'utilisateur a explicitement demandé que ce schéma soit utilisé en cliquant sur cette colonne, soit le schéma a été automatiquement associé en fonction d'un `targetNamespace` correspondant.

- **N’utilisez pas les schémas sélectionnés**. Ce schéma n'est pas utilisé par le document actif, même si le schéma a un `targetNamespace` correspondant. Ce paramètre peut être utile dans la résolution de conflits, lorsqu'il existe plusieurs versions du même schéma dans le cache de schéma ou dans la solution.

**Espace de noms cible**

Affiche l'espace de noms cible associé au schéma XML.

**Nom de fichier**

Affiche le nom de fichier du schéma XML.

**Ajouter**

Ouvre la boîte de dialogue **ouvrir le schéma XSD** , qui vous permet de sélectionner des schémas supplémentaires à ajouter au jeu de schémas. Lorsque vous ajoutez un schéma au jeu de schémas, la valeur de colonne **use** est définie pour **utiliser ce schéma**.

**Supprimer**

Supprime le schéma actuellement sélectionné du jeu de schémas. Cela supprime le schéma du cache de schémas en mémoire, mais pas du système de fichiers.

## <a name="see-also"></a>Voir aussi

- [Procédure : sélectionner les schémas XML à utiliser](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Cache de schéma](../xml-tools/schema-cache.md)
