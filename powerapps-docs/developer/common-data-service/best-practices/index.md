---
title: 開発者:Common Data Service for Apps のベスト プラクティスとガイダンス | Microsoft Docs
description: PowerApps での Common Data Service for Apps の開発者向けベスト プラクティスとガイダンス
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/07/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bf449f801e4e7617e7fe91d0884b3443559e71c6
ms.sourcegitcommit: 11486fb4c16095e3fef785126003cac3e3e06c0d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2019
ms.locfileid: "54271437"
---
# <a name="best-practices-and-guidance-for-the-common-data-service-for-apps"></a>Common Data Service for Apps のベスト プラクティスとガイダンス

Common Data Service (CDS) for Apps (CDS) は、高度にカスタマイズされ、調整されたエクスペリエンスを開発者が構築できるようになる拡張可能なフレームワークです。 開発者が Common Data Service (CDS) for Apps を使用してカスタマイズ、拡張、または統合を行う場合は、確立されたガイダンスとベスト プラクティスに留意することをお勧めします。 

ここでは、Microsoft が特定した問題とその影響について学び、その問題を解決するためのガイダンスを理解してください。 これから、特定の方法で処理を実行する理由に関する背景について説明し、今後発生する可能性がある問題を回避します。 これにより、お客様の環境のユーザビリティ、サポータビリティ、パフォーマンスが向上します。 このガイダンス ドキュメントは、開発者および管理者ガイド内の既存の情報をサポートしています。

# <a name="targeted-customization-types"></a>対象となるカスタマイズの種類
このドキュメントでは、以下のカスタマイズの種類を対象としています。

- カスタム ワークフロー アクティビティとプラグイン
- CDS データの操作
- Common Data Service for Apps を拡張する統合

# <a name="sections"></a>セクション
各ガイダンス記事には、以下のセクションのほとんどまたはすべてが含まれています。

- タイトル - ガイダンスの説明
- カテゴリ - ガイダンスに従わない場合に影響を受ける 1 つ以上の領域
- 影響の可能性 - ガイダンスに従わない場合に環境に及ぼす影響のリスク レベル (高、中、低)
- 現象 - ガイダンスに従わなかったことを示す可能性があるもの
- ガイダンス - 推奨事項 (例も含まれる可能性があります)
- 問題のパターン - ガイダンスに従っていないことの説明または例
- その他の情報 - より広範な見方のための補足情報
- 関連項目 - 記事に記載されている内容の詳細情報の参照先

# <a name="categories"></a>カテゴリ
各ガイダンス記事は、以下のカテゴリの 1 つ以上に分類されます。

- 使用方法 - 特定の API、パターン、または構成の不適切な使用方法
- 設計 - カスタマイズの設計上の欠陥
- パフォーマンス - メモリ管理、CPU 使用率、ネットワーク トラフィック、ユーザー エクスペリエンスなどの領域でパフォーマンスに悪影響を及ぼす可能性があるカスタマイズまたはパターン
- セキュリティ - ランタイム環境で悪用される可能性があるカスタマイズの潜在的な脆弱性
- Upgrade Readiness - バージョンのアップグレードに失敗するリスクが高くなる可能性があるカスタマイズまたはパターン
- オンラインの移行 - オンラインの移行に失敗するリスクが高くなる可能性があるカスタマイズまたはパターン
- 保守性 - 変更を加えるために必要な開発者の作業量、必要な変更の頻度、または退行を招く可能性が不必要に増加するカスタマイズ
- サポータビリティ - 削除された API の使用や禁止されたテクノロジの実装など、公開されているサポータビリティ ステートメントの範囲から外れるカスタマイズまたはパターン