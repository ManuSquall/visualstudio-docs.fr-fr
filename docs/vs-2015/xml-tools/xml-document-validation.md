---
title: Validation de document XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ee5d3cff260346a5bcc1806b09b955642c608f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669492"
---
# <a name="xml-document-validation"></a>Validation de documents XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'éditeur XML vérifie la syntaxe XML 1.0 et effectue une validation des données en cours de frappe. L'éditeur peut effectuer cette validation à l'aide d'une définition de type de document (DTD) ou d'un schéma. Des soulignements ondulés rouges marquent les erreurs XML 1.0 correctement construites. Des soulignements ondulés bleus marquent les erreurs sémantiques d'après la validation de la DTD ou du schéma. La liste d'erreurs comporte une entrée pour chaque erreur détectée. Vous pouvez également afficher le message d'erreur en plaçant le curseur sur la ligne ondulée.

 Les schémas utilisés pour la validation sont recherchés en fonction de la comparaison du `targetNamespace` d’un schéma compilé à la déclaration xmlns de l’élément. Les schémas compilés sont chargés à partir d'un des emplacements suivants, répertoriés par ordre de priorité :

- À partir du nom de fichier spécifié dans le champ **schémas** de la fenêtre Propriétés de document.

- Une DTD ou un schéma inline

- Une DTD externe ou un attribut `xsd:schemaLocation` et `xsd:noNamespaceSchemaLocation`

- Un URI d'espace de noms de schéma XDR « x-schema »

  Des schémas peuvent également être recherchés dans les emplacements supplémentaires suivants lorsque le schéma contient un espace de noms cible non vide :

- Une autre fenêtre d'éditeur qui contient le schéma

- Un schéma contenu dans la solution actuelle

- Un schéma du répertoire de cache de schéma

## <a name="xslt-files"></a>Fichiers XSLT
 Lorsque vous modifiez un fichier XSLT, le fichier xslt.xsd situé du cache de schéma est utilisé pour la validation. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. Les erreurs provenant du compilateur XSLT sont signalées par des soulignements ondulés rouges.

## <a name="xml-schema-xsd-files"></a>Fichiers XSD (XML schema definition)
 Lorsque vous modifiez un fichier de schéma XML, le fichier xsdschema.xsd situé dans le cache de schéma est utilisé pour la validation. Les erreurs de validation sont indiquées par des soulignements ondulés bleus. Les erreurs de compilation sont signalées de la même façon.

## <a name="see-also"></a>Voir aussi
 [Éditeur XML](../xml-tools/xml-editor.md)
