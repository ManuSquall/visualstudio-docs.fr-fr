---
title: DémontageData (en anglais) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737288"
---
# <a name="disassemblydata"></a>DisassemblyData
Décrit une instruction de démontage pour l’environnement de développement intégré (IDE) à afficher.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Membres
`dwFields`\
La [constante DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) qui précise quels champs sont remplis.

`bstrAddress`\
L’adresse comme un décalage à partir d’un point de départ (généralement le début de la fonction associée).

`bstrCodeBytes`\
Le code est enseille pour cette instruction.

`bstrOpcode`\
L’opcode pour cette instruction.

`bstrOperands`\
Les opérandes pour cette instruction.

`bstrSymbol`\
Le nom du symbole, le cas échéant, associé à l’adresse (symbole public, étiquette, et ainsi de suite).

`uCodeLocationId`\
L’identifiant de localisation du code pour cette ligne démontée. Si l’adresse de contexte de code d’une ligne est supérieure à l’adresse de contexte de code d’une autre, l’identifiant de localisation de code démonté de la première sera également supérieur à l’identifiant de localisation du code de la seconde.

`posBeg`\
Le [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui correspond à la position dans un document où les données de démontage commence.

`posEnd`\
Le [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) qui correspond à la position dans un document où les données de démontage se terminent.

`bstrDocumentUrl`\
Pour les documents texte qui peuvent être `bstrDocumentUrl` représentés comme noms de fichiers, le champ est `file://file name`rempli avec le nom de fichier où la source peut être trouvée, en utilisant le format .

Pour les documents texte qui ne `bstrDocumentUrl` peuvent pas être représentés comme noms de fichiers, est un identifiant unique pour le document, et le moteur de débogé doit implémenter la méthode [GetDocument.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)

Ce champ peut également contenir des informations supplémentaires sur les contrôles. Pour plus de détails, consultez la section Notes.

`dwByteOffset`\
Le nombre d’octets de l’instruction est depuis le début de la ligne de code.

`dwFlags`\
La [constante DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) qui précise quels drapeaux sont actifs.

## <a name="remarks"></a>Notes
Chaque `DisassemblyData` structure décrit une instruction de démontage. Un éventail de ces structures est retourné de la méthode [Read.](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)

La structure [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) est utilisée uniquement pour les documents textuels. La plage de code source pour cette instruction est remplie uniquement pour la `dwByteOffset == 0`première instruction générée à partir d’une déclaration ou d’une ligne, par exemple, quand .

Pour les documents qui ne sont pas textuels, un contexte `bstrDocumentUrl` de document peut être obtenu à partir du code, et le champ doit être une valeur nulle. Si `bstrDocumentUrl` le champ est `bstrDocumentUrl` le même `DisassemblyData` que le champ `bstrDocumentUrl` dans l’élément de tableau précédent, puis définissez la valeur nulle.

Si `dwFlags` le champ `DF_DOCUMENT_CHECKSUM` a le drapeau fixé, puis des informations `bstrDocumentUrl` supplémentaires checksum suit la chaîne pointée par le champ. Plus précisément, après le terminateur de la chaîne nulle, il suit un GUID identifiant l’algorithme de checksum qui est à son tour suivi d’une valeur de 4 octets indiquant le nombre d’octets dans le checksum et qui à son tour est suivie par les bytes checksum. Voir l’exemple dans ce sujet sur la façon [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]d’encoder et décoder ce champ dans .

## <a name="example"></a>Exemple
Le `bstrDocumentUrl` champ peut contenir des informations `DF_DOCUMENT_CHECKSUM` supplémentaires autres qu’une chaîne si le drapeau est défini. Le processus de création et de lecture [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]de cette chaîne codée est simple dans . Cependant, [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]dans , c’est une autre question. Pour ceux qui sont curieux, l’exemple suivant montre une [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] façon de créer la chaîne codée à partir et une façon de décoder la chaîne codée dans [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)].

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Lire](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
