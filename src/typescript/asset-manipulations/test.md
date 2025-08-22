---
order: -3
icon: arrow-switch
---

# Asset Conversions22222222222222

+++ TypeScript
{% capture VestsDescriptionTS %}
The vestsToHp method converts VESTS into Hive Power (HP).  
It requires three `NaiAsset` instances: one for the VESTS and two for the total vesting fund Hive and total vesting shares.
{% endcapture %}

{% capture HbdDescriptionTS %}
The hbdToHive method converts HBD into Hive.  
It requires three `NaiAsset` instances: one for the HBD, one for the base (another HBD asset), and one for the quote (a HIVE asset).
{% endcapture %}

## Using `vestsToHp`
{{ VestsDescriptionTS }}
:::code source="../../static/snippets/src/typescript/asset-manipulations/asset-convertions/vests-to-hp.ts" language="typescript" title="Test it yourself on StackBlitz" :::

## Using `hbdToHive`
{{ HbdDescriptionTS }}
:::code source="../../static/snippets/src/typescript/asset-manipulations/asset-convertions/hbd-to-hive.ts" language="typescript" title="Test it yourself on StackBlitz" :::

+++ Python
{% capture VestsDescriptionPy %}
The vests_to_hp method converts VESTS into Hive Power (HP).  
It requires three `NaiAsset` instances: one for the VESTS and two for the total vesting fund Hive and total vesting shares.
{% endcapture %}

{% capture HbdDescriptionPy %}
The hbd_to_hive method converts HBD into Hive.  
It requires three `NaiAsset` instances: one for the HBD, one for the base (another HBD asset), and one for the quote (a HIVE asset).
{% endcapture %}

## Using `vests_to_hp`
{{ VestsDescriptionPy }}
:::code source="../../static/snippets/src/python/asset-manipulations/asset-conversion/vests_to_hp.py" language="python" title="Test it yourself on Codespace" :::

## Using `hbd_to_hive`
{{ HbdDescriptionPy }}
:::code source="../../static/snippets/src/python/asset-manipulations/asset-conversion/hbd_to_hive.py" language="python" title="Test it yourself on Codespace" :::
