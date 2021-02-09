---
title: Inscription d’un Service2 de langage hérité | Microsoft Docs
description: Cet article répertorie les entrées de Registre pour les différentes options de service de langage disponibles dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d08552683ce61892b0ee233173466a79326e4c6f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894853"
---
# <a name="registering-a-legacy-language-service-2"></a>Inscription d’un service de langage hérité 2
Les sections suivantes fournissent des listes d’entrées de Registre pour les différentes options de service de langage disponibles dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Dans la liste suivante d’entrées de Registre, *vs reg root* est égal à HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *x. y*, où *x. y* est le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] numéro de version.

## <a name="registry-entries-for-language-service-options"></a>Entrées de Registre pour les options du service de langage
 La clé de nom de langue des services \Languages\Language *racine vs reg* \\  peut contenir les valeurs suivantes.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ|*\<GUID>*|GUID du service de langage.|
|LangResID|REG_DWORD|0x0-0xFFFF|Identificateur de ressource de chaîne (ResID) pour le nom de texte localisé de la langue.|
|Package|REG_SZ|*\<GUID>*|GUID du VSPackage.|
|ShowCompletion|REG_DWORD|0-1|Spécifie si les options de **saisie semi-automatique des instructions** dans la boîte de dialogue **options** sont activées.|
|ShowSmartIndent|REG_DWORD|0-1|Spécifie si l’option permettant de sélectionner la mise en retrait **intelligente** dans la boîte de dialogue **options** est activée.|
|RequestStockColors|REG_DWORD|0-1|Spécifie si les couleurs personnalisées ou par défaut sont utilisées pour colorier les mots clés.|
|ShowHotURLs|REG_DWORD|0-1|Spécifie si l’utilisateur peut cliquer sur les URL.|
|URL par défaut non réactives|REG_DWORD|0-1|Spécifie le paramètre initial de l’option de **navigation activer l’URL par simple clic** dans la boîte de dialogue **options** .|
|DefaultToInsertSpaces|REG_DWORD|0-1|Spécifie si le service de langage a « espaces d’insertion » comme option de tabulation par défaut.|
|ShowDropdownBarOption|REG_DWORD|0-1|Active ou désactive l’option **barre de navigation** dans la boîte de dialogue **options** qui affiche ou masque la **barre de navigation**.|
|Seule fenêtre de code|REG_DWORD|0-1|Active ou désactive le nouveau choix de **fenêtre** dans le menu **fenêtre** pour un service de langage.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|Active ou désactive le paramètre de la boîte de dialogue **options** pour **Masquer les membres avancés**.|
|CF_HTML de support|REG_DWORD|0-1|Spécifie si l’éditeur permet la copie et le collage de données HTML.|
|EnableLineNumbersOption|REG_DWORD|0-1|Spécifie si les options des **numéros de ligne** dans la boîte de dialogue **options** sont activées pour un service de langage.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Spécifie si les membres avancés, tels que les champs privés, sont masqués dans les listes de saisie semi-automatique.|
|ShowBraceCompletion|REG_DWORD|0-1|Spécifie si l’option d’achèvement de l' **accolade** dans la boîte de dialogue **options** est activée.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
        LangResID             = reg_dword:0x00000000
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}
        ShowCompletion        = reg_dword:0x00000001
        ShowSmartIndent       = reg_dword:0x00000001
        ShowDropdownBarOption = reg_dword:0x00000001
```

## <a name="registry-entries-for-debugger-languages-options"></a>Entrées de Registre pour les options des langues du débogueur
 Le nom du langage \Languages\Language services *racine de vs reg* \\ \Debugger *Language* \\ *GUID*\ Key peut inclure les valeurs suivantes.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ|texte|La valeur par défaut peut être utilisée pour documenter le nom de la langue. Le nom de cette clé est un GUID d’un évaluateur d’expression qui a une entrée correspondante dans l' *\<VS Reg Root>* évaluateur \AD7Metrics\Expression.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>Entrées de Registre pour les options des outils de l’éditeur
 Vous pouvez ajouter des clés de Registre sous la clé EditorToolsOptions pour les pages de propriétés et les nœuds de propriété. Ces clés et leurs valeurs identifient les pages de propriétés dans la boîte de dialogue **options** (dans le menu **Outils** ) utilisées pour configurer le service de langage. Dans l’exemple suivant, le nom de la *page* est le nom d’une page de propriétés, et le nom du *nœud* est le nom d’un nœud dans l’arborescence de la boîte de dialogue **options** . L’entrée de page et l’entrée de nœud doivent être spécifiées séparément.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ|ResID|Nom complet localisé de cette page d’options. Le nom peut être un texte littéral ou # `nnn` , où `nnn` est un ID de ressource de chaîne dans la DLL satellite du VSPackage spécifié.|
|Package|REG_SZ|*GUID*|GUID du VSPackage qui implémente cette page d’options.|
|Page|REG_SZ|*GUID*|GUID de la page de propriétés à demander à partir du VSPackage en appelant la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> méthode. Si cette entrée de Registre n’est pas présente, la clé de registre décrit un nœud, pas une page.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      CSharp\
        EditorToolsOptions\
          Formatting\
            (Default) = reg_sz:#242
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
            General\
              (Default) = reg_sz:#255
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}
            Indentation\
              (Default) = reg_sz:#250
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}
            Newlines\
              (Default) = reg_sz:#253
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}
```

## <a name="registry-entries-for-file-name-extension-options"></a>Entrées de Registre pour les options d’extension de nom de fichier
 L’entrée de l’extension de fichier doit inclure le point de début, par exemple « . myext ».

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ|*GUID*|GUID du service pour le service de langage par défaut pour ce type d’extension de nom de fichier.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Entrées de Registre pour les options de l’éditeur
 La clé de \Editors *racine de vs reg* peut contenir les valeurs suivantes :

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ|""|Inutilisé vous pouvez placer votre nom ici pour la documentation.|
|DefaultToolboxTab|REG_SZ|""|Nom de l’onglet Boîte à outils à utiliser par défaut lorsque l’éditeur est actif.|
|DisplayName|REG_SZ|ResID|Nom à afficher dans la boîte de dialogue **Ouvrir avec** . Le nom est l’ID de ressource de chaîne ou un nom au format standard.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Utilisé pour la commande de menu **Ouvrir avec** . Si vous ne souhaitez pas répertorier l’éditeur de texte par défaut dans la liste des éditeurs disponibles pour un type de fichier spécifique, définissez cette valeur sur 1.|
|LinkedEditorGUID|REG_SZ|*\<GUID>*|Utilisé pour tous les services de langage qui peuvent ouvrir un fichier avec prise en charge de la page de codes. Par exemple, lorsque vous ouvrez un fichier. txt à l’aide de la commande **Ouvrir avec** , des options sont fournies pour l’utilisation de l’éditeur de code source avec et sans encodage.<br /><br /> Le GUID spécifié dans le nom de la sous-clé est pour la fabrique d’éditeur CodePage ; le GUID lié spécifié dans cette entrée de Registre spécifique est pour la fabrique d’éditeur standard. L’objectif de cette entrée est que si l’IDE n’ouvre pas un fichier à l’aide de l’éditeur par défaut, l’IDE essaiera d’utiliser l’éditeur suivant dans la liste. Cet éditeur suivant ne doit pas être la fabrique d’éditeur de page de codes, car cette fabrique d’éditeur est fondamentalement identique à la fabrique d’éditeur qui a échoué.|
|Package|REG_SZ|*\<GUID>*|GUID du VSPackage pour le ResID du nom d’affichage.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      (Default)            = reg_sz:Html Editor with Encoding
      DefaultToolboxTab    = reg_sz:HTML
      DisplayName          = reg_sz:#20101
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}
```

## <a name="registry-entries-for-logical-view-options"></a>Entrées de Registre pour les options de vue logique
 L’interface utilisateur graphique de l’éditeur \Editors *racine vs Reg* \\ *>* la clé \LogicalViews peut contenir les valeurs suivantes.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ||Inutilisé.|
|*\<GUID>*|REG_SZ|""|Clé des affichages logiques pris en charge. Vous pouvez en avoir autant que vous le souhaitez. Le nom de l’entrée de Registre est ce qui est important, et non la valeur, qui est toujours une chaîne vide.|

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      LogicalViews\
       (Default) = reg_sz:
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
```

## <a name="registry-entries-for-editor-extension-options"></a>Entrées de Registre pour les options d’extension de l’éditeur
 La clé \Extensions GUID de l’éditeur \Editors *racine vs reg* \\ peut contenir les valeurs suivantes. L’extension de nom de fichier n’inclut pas le point de début.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|(Par défaut)|REG_SZ||Inutilisé.|
|*\<ext>*|REG_DWORD|0-0xFFFFFFFF|Priorité relative des extensions. Si deux ou plusieurs langues partagent la même extension, la langue de priorité la plus élevée est choisie.|

 En outre, la sélection par défaut de l’utilisateur actuel pour un éditeur est stockée dans HKEY_Current_User \Software\Microsoft\VisualStudio \\ *X. Y*\Default Editors \\ *ext*. Le GUID du service de langage sélectionné se trouve dans l’entrée personnalisée. Cela est prioritaire pour l’utilisateur actuel.

### <a name="example"></a>Exemple

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      Extensions\
       (Default) = reg_sz:
       *         = reg_dword:0x00000018
       html      = reg_dword:0x00000027
       shtm      = reg_dword:0x00000027
       shtml     = reg_dword:0x00000027
```

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Entrées de Registre pour les options du service de langage du package managé
 Les entrées de Registre suivantes sont spécifiques aux classes du service de langage MPF (Managed package Framework). Ces entrées de Registre indiquent la prise en charge dans le service de langage pour différentes fonctionnalités IntelliSense et pour d’autres fonctionnalités d’édition avancées.

 Ces entrées de Registre sont accessibles par le biais de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.

|Nom|Type|Plage|Description|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Prise en charge des opérations IntelliSense.|
|MatchBraces|REG_DWORD|0-1|Prise en charge des paires de langues correspondantes telles que les accolades, les parenthèses et les crochets.|
|Info express|REG_DWORD|0-1|Prise en charge de l’opération Info Express IntelliSense.|
|ShowMatchingBrace|REG_DWORD|0-1|Prise en charge de l’affichage de la paire de langues correspondante dans la barre d’État.|
|MatchBracesAtCaret|REG_DWORD|0-1|Prise en charge de l’affichage des paires de langues correspondantes, en général en mettant en surbrillance les deux éléments.|
|MaxErrorMessages|REG_DWORD|0-n|Nombre maximal d’erreurs qui peuvent être affichées dans la fenêtre de **liste d’erreurs** .|
|CodeSenseDelay|REG_DWORD|0-n|Nombre de millisecondes à attendre avant de lancer une analyse en arrière-plan pour une opération IntelliSense.|
|EnableAsyncCompletion|REG_DWORD|0-1|Prise en charge de l’analyse en arrière-plan.|
|EnableCommenting|REG_DWORD|0-1|La prise en charge des commentaires sur les blocs de texte sélectionnés et implique également la prise en charge de l’ajout de commentaires au texte sélectionné.|
|EnableFormatSelection|REG_DWORD|0-1|Prise en charge de la mise en forme du texte, telle que la mise en retrait automatique ou le réglage de la position des accolades.|
|AutoOutlining|REG_DWORD|0-1|Prise en charge du mode plan (régions pouvant être réduites).|
|MaxRegions|REG_DWORD|0-n|Nombre maximal de zones masquées par fichier.|

```
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      XML\
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}
        MatchBraces           = reg_dword:0x00000001
        QuickInfo             = reg_dword:0x00000001
        ShowMatchingBrace     = reg_dword:0x00000001
        MatchBracesAtCaret    = reg_dword:0x00000000
        MaxErrorMessages      = reg_dword:0x00000064
        CodeSenseDelay        = reg_dword:0x000001f4
        MaxRegions            = reg_dword:0x0000000a
```

## <a name="see-also"></a>Voir aussi
- [Développement d’un service de langage hérité](../../extensibility/internals/developing-a-legacy-language-service.md)
