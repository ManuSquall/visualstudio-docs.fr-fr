---
title: Informations sur l’exécution du contrôle des sources (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92ce5e822ec7360b3b1a4010d250a4349443c142
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705041"
---
# <a name="source-control-runtime-details"></a>Détails du Runtime du contrôle de code source
Un projet est ajouté au contrôle source lorsque l’utilisateur ajoute un fichier dans le projet pour le contrôle source, ou par l’intermédiaire d’un contrôleur d’automatisation, comme un assistant. Un projet ne précise pas pour lui-même qu’il est sous contrôle source; il prend en charge le contrôle des sources, mais doit y être ajouté manuellement.

## <a name="registering-with-a-source-control-package"></a>Enregistrement avec un forfait de contrôle des sources
 Lorsqu’un fichier de votre projet est ajouté <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> au contrôle des sources, l’environnement appelle pour vous fournir quatre chaînes opaques qui sont utilisées comme cookies par le système de contrôle source. Rangez ces chaînes dans votre dossier de projet. Ces chaînes doivent être transmises au Source Control Stub (le composant Visual Studio qui <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>gère les paquets de contrôle des sources) sur le démarrage du type de projet en appelant . Cela charge à son tour le paquet de contrôle source `IVsSccManager2::RegisterSccProject`approprié et transmet l’appel à sa mise en œuvre de .

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)
