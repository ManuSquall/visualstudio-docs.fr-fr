---
title: Extraits de code Visual C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4655ea7160d353fc8735a9025f36de368f247ba8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65698187"
---
# <a name="visual-c-code-snippets"></a>Extraits de code Visual C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les extraits de code sont des extraits prêts à l’emploi que vous pouvez rapidement insérer dans votre code. Par exemple, l’extrait de code `for` crée une boucle `for` vide. Certains extraits de code sont des extraits « Entourer de ». Il vous permettent de sélectionner des lignes de code, puis de choisir un extrait de code qui incorpore les lignes sélectionnées. Par exemple, quand vous sélectionnez des lignes de code et que vous activez l’extrait de code `for`, cela crée une boucle `for` avec ces lignes de code dans le bloc de boucle. Les extraits de code peuvent accélérer, simplifier et fiabiliser l’écriture de code de programme.  
  
 Vous pouvez insérer un extrait de code à l’emplacement du curseur, ou insérer un extrait de code « Entourer de » autour du code actuellement sélectionné. L’outil d’insertion d’extraits de code est appelé par le biais de la commande **Insérer un extrait de code** ou **Entourer de** du menu **IntelliSense**, ou à l’aide des raccourcis clavier Ctrl+K puis X, ou Ctrl+K puis S, respectivement.  
  
 L’outil d’insertion d’extraits de code affiche le nom de l’extrait de code pour tous les extraits de code disponibles. Il inclut également une boîte de dialogue d’entrée où vous pouvez taper le nom de l’extrait de code, ou une partie du nom. Il met en évidence la correspondance la plus proche avec un nom d’extrait de code. Une pression sur la touche Tab à tout moment fait disparaître l’outil d’insertion d’extraits de code et insère l’extrait de code sélectionné. Une pression sur la touche Échap ou un clic sur le bouton de la souris dans l’Éditeur de code fait disparaître l’outil d’insertion d’extraits de code sans insérer d’extrait de code.  
  
## <a name="default-code-snippets"></a>Extraits de code par défaut  
 Par défaut, les extraits de code suivants sont inclus dans Visual Studio.  
  
|Nom (ou raccourci)|Description|Emplacements valides où insérer l’extrait de code|  
|--------------------------|-----------------|---------------------------------------|  
|#if|Crée une directive [#if](https://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2) et une directive [#endif](https://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05).|N’importe où.|  
|#region|Crée une directive [#region](https://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4) et une directive [#endregion](https://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526).|N’importe où.|  
|~|Crée un destructeur pour la classe conteneur.|Dans une classe.|  
|Attribut|Crée une déclaration pour une classe qui dérive de <xref:System.Attribute>.|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|  
|checked|Crée un bloc [checked](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|class|Crée une déclaration de classe.|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|  
|ctor|Crée un constructeur pour la classe conteneur.|Dans une classe.|  
|cw|Crée un appel à <xref:System.Console.WriteLine%2A>.|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|do|Crée une boucle [do](https://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb)`while`.|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|else|Crée un bloc [else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|enum|Crée une déclaration [enum](https://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c).|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|  
|equals|Crée une déclaration de méthode qui substitue la méthode <xref:System.Object.Equals%2A> définie dans la classe <xref:System.Object>.|Dans une classe ou un struct.|  
|exception|Crée une déclaration pour une classe qui dérive d’une exception (<xref:System.Exception> par défaut).|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|  
|for|Crée une boucle [for](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|foreach|Crée une boucle [foreach](https://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|forr|Crée une boucle [for](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) qui décrémente la variable de boucle après chaque itération.|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|if|Crée un bloc [if](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|indexer|Crée une déclaration d’indexeur.|Dans une classe ou un struct.|  
|interface|Crée une déclaration [interface](https://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba).|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|  
|invoke|Crée un bloc qui appelle un événement en toute sécurité.|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|iterator|Crée un itérateur.|Dans une classe ou un struct.|  
|iterindex|Crée une paire itérateur/indexeur « named » à l’aide d’une classe imbriquée.|Dans une classe ou un struct.|  
|lock|Crée un bloc [lock](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|mbox|Crée un appel à <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Vous devrez peut-être ajouter une référence à System.Windows.Forms.dll.|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|namespace|Crée une déclaration [namespace](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f).|Dans un espace de noms (notamment l’espace de noms global).|  
|prop|Crée une déclaration de [propriété implémentée automatiquement](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).|Dans une classe ou un struct.|  
|propfull|Crée une déclaration de propriété avec des accesseurs get et set.|Dans une classe ou un struct.|  
|propg|Crée une [propriété implémentée automatiquement](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) en lecture seule avec un accesseur « set » privé.|Dans une classe ou un struct.|  
|sim|Crée une déclaration de méthode Main [static](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[int](https://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52).|Dans une classe ou un struct.|  
|struct|Crée une déclaration [struct](https://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c).|Dans un espace de noms (notamment l’espace de noms global), une classe ou un struct.|  
|svm|Crée une déclaration de méthode Main [static](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[void](https://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4).|Dans une classe ou un struct.|  
|switch|Crée un bloc [switch](https://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|try|Crée un bloc [try-catch](https://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|tryf|Crée un bloc [try-finally](https://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|unchecked|Crée un bloc [unchecked](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|unsafe|Crée un bloc [unsafe](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
|using|Crée une directive [using](https://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8).|Dans un espace de noms (notamment l’espace de noms global).|  
|while|Crée une boucle [while](https://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59).|Dans une méthode, un indexeur, un accesseur de propriété ou un accesseur d’événement.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions des extraits de code](../ide/code-snippet-functions.md)   
 [Extraits de code](../ide/code-snippets.md)   
 [Guide pratique pour Créer un nouvel extrait de code avec remplacements](https://msdn.microsoft.com/8d56d43c-097a-475b-aa85-cae1554b6338)   
 [Paramètres de modèle](../ide/template-parameters.md)   
 [Guide pratique pour Utiliser des extraits de Code entourer de](../ide/how-to-use-surround-with-code-snippets.md)   
 [Guide pratique pour restaurer les extraits de code de refactorisation C#](../ide/how-to-restore-csharp-refactoring-snippets.md)
