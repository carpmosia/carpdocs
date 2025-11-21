{% macro img(path, map) %}
{% if map %}
<a target="_blank" href="/assets/images/mapping/{{path}}/{{map}}.webp"><img src="/assets/images/mapping/{{path}}/{{map}}.webp" style="width: 100%; object-fit: contain; aspect-ratio: 1; image-rendering: pixelated;"></a>
{% endif %}
{% endmacro img %}

{% macro table(title, maps, names, path) %}
<div class="table-wrapper" style="text-align: center; width: 100%">
<table>
<thead>
<tr><th></th><th>{{ title }}</th><th></th></tr>
</thead>
<tbody>
{% for i in range(end=maps | length, step_by=3) %}
<tr style="width: 100%;">
<td style="width: 33%;"><strong>{{ names | nth(n=i) }}</strong></td>
<td style="width: 33%;"><strong>{{ names | nth(n=i + 1) }}</strong></td>
<td style="width: 33%;"><strong>{{ names | nth(n=i + 2) }}</strong></td>
</tr>
<tr style="width: 100%;">
<td style="width: 33%;">{{ self::img(path=path, map=maps | nth(n=i)) }}</td>
<td style="width: 33%;">{{ self::img(path=path, map=maps | nth(n=i + 1)) }}</td>
<td style="width: 33%;">{{ self::img(path=path, map=maps | nth(n=i + 2)) }}</td>
</tr>
{% endfor %}
</tbody></table>
</div>
{% endmacro table %}

{% macro examples(path) %}
{{ self::table(
  title="In Rotation",
  maps=["amber", "bagel", "box", "elkridge", "feint", "fland", "marathon", "oasis-2", "saltern-2", "packed", "plasma", "exo"],
  names=["Amber", "Bagel", "Box", "Elkridge", "Feint", "Fland", "Marathon", "Oasis 2", "Saltern 2", "Packed", "Plasma", "Exo"],
  path=path
)}}
These maps are derotated and likely very outdated, not recommended to use for reference.
{{ self::table(
  title="Derotated",
  maps=["aspid", "barratry", "cluster", "cog", "core", "gate", "gemini", "loop", "meta", "oasis", "omega", "saltern", "train"],
  names=["Aspid", "Barratry", "Cluster", "Cog", "Core", "Gate", "Gemini", "Loop", "Meta", "Oasis", "Omega", "Saltern", "Train"],
  path=path
)}}
These maps are work-in-progress, don't judge them yet :3c
{{ self::table(
  title="Work In Progress",
  maps=["elkridge-2", "senpeak", "serpentcrest", "thunderchild", "tram", "waterjug"],
  names=["Elkridge 2", "Serenity Peak", "Serpentcrest", "Thunderchild", "Tram", "Waterjug"],
  path=path
)}}
{% endmacro examples %}

{% macro shuttle_examples(path) %}
{{ self::table(
  title="In Rotation",
  maps=["generic", "elkridge", "exo", "fland", "plasma"],
  names=["Generic", "Elkridge", "Exo", "Fland", "Plasma"],
  path=path
)}}
These shuttles belong to derotated and likely very outdated maps, not recommended to use for reference.
{{ self::table(
  title="Derotated",
  maps=["core", "relic"],
  names=["Core", "Relic"],
  path=path
)}}
These shuttles belong to work-in-progress maps, don't judge them yet :3c
{{ self::table(
  title="Work In Progress",
  maps=["senpeak"],
  names=["Serenity Peak"],
  path=path
)}}
{% endmacro shuttle_examples %}
