# pySigma Pipeline Examples

This directory contains comprehensive, working examples of all pySigma processing pipeline components. Each example includes a complete pipeline configuration and a test Sigma rule to validate functionality.

## Quick Start

To test any example, use the `sigma convert` command:

```bash
sigma convert -t <backend> -p <pipeline-file> <rule-file>
```

### Example Command

```bash
# Test the embed postprocessing example with Splunk backend
sigma convert -t splunk -p query_postprocessing_transformations/embed/pipeline.yml query_postprocessing_transformations/embed/rule.yml
```

## Directory Structure

### [Query Postprocessing Transformations](./query_postprocessing_transformations/)

Query postprocessing transformations modify individual queries **AFTER** backend conversion but **BEFORE** finalization.

- **[embed](./query_postprocessing_transformations/embed/)** - Wraps queries with prefix and/or suffix strings
- **[simple_template](./query_postprocessing_transformations/simple_template/)** - Applies Python format string templates to queries
- **[template](./query_postprocessing_transformations/template/)** - Applies Jinja2 templates with conditional logic and loops
- **[json](./query_postprocessing_transformations/json/)** - Embeds queries into JSON structures
- **[replace](./query_postprocessing_transformations/replace/)** - Performs regex-based find and replace on queries
- **[nest](./query_postprocessing_transformations/nest/)** - Sequential multi-step postprocessing (see folder for notes on limitations)

### [Finalizers](./finalizers/)

Finalizers transform the **entire list** of converted queries into final output format.

- **[concat](./finalizers/concat/)** - Concatenates all queries with separators and optional prefix/suffix
- **[json](./finalizers/json/)** - Outputs queries as JSON array
- **[yaml](./finalizers/yaml/)** - Outputs queries as YAML list
- **[template](./finalizers/template/)** - Applies Jinja2 template to entire query list
- **[nested](./finalizers/nested/)** - Sequential multi-step finalization

### [Transformations](./transformations/)

Transformations modify Sigma rules **BEFORE** backend conversion. These apply to fields, values, conditions, and other rule components.

#### Field Transformations

- **[field_name_mapping](./transformations/field_name_mapping/)** - Maps field names to different field names
- **[field_name_prefix_mapping](./transformations/field_name_prefix_mapping/)** - Maps field name prefixes to different prefixes
- **[field_name_prefix](./transformations/field_name_prefix/)** - Adds prefix to field names
- **[field_name_suffix](./transformations/field_name_suffix/)** - Adds suffix to field names
- **[add_field](./transformations/add_field/)** - Adds new field with value to detection items
- **[remove_field](./transformations/remove_field/)** - Removes fields from detection items
- **[set_field](./transformations/set_field/)** - Sets field values in detection items
- **[hashes_fields](./transformations/hashes_fields/)** - Handles hash algorithm field name transformations

#### Condition Transformations

- **[add_condition](./transformations/add_condition/)** - Adds new conditions to detection items

#### Value Transformations

- **[replace_string](./transformations/replace_string/)** - Replaces strings in field values using regex
- **[map_string](./transformations/map_string/)** - Maps string values to different values
- **[regex](./transformations/regex/)** - Applies regex transformations to field values
- **[set_value](./transformations/set_value/)** - Sets specific values for fields
- **[convert_type](./transformations/convert_type/)** - Converts value types (e.g., string to number)
- **[case](./transformations/case/)** - Changes case of field values (upper/lower)

#### Rule Metadata Transformations

- **[change_logsource](./transformations/change_logsource/)** - Modifies rule logsource definitions
- **[set_custom_attribute](./transformations/set_custom_attribute/)** - Sets custom attributes on rules
- **[set_state](./transformations/set_state/)** - Sets custom state values accessible in later transformations

#### Rule Processing Control

- **[drop_detection_item](./transformations/drop_detection_item/)** - Removes detection items matching conditions
- **[rule_failure](./transformations/rule_failure/)** - Causes rule conversion to fail with message
- **[detection_item_failure](./transformations/detection_item_failure/)** - Causes detection item conversion to fail with message

#### Placeholder Transformations

- **[wildcard_placeholders](./transformations/wildcard_placeholders/)** - Defines placeholders for wildcards in values
- **[value_placeholders](./transformations/value_placeholders/)** - Replaces placeholders in values with actual values
- **[query_expression_placeholders](./transformations/query_expression_placeholders/)** - Replaces placeholders with query expressions

## File Structure

Each example folder contains:

- `pipeline.yml` - The processing pipeline configuration
- `rule.yml` - A test Sigma rule to validate the pipeline

## Version Compatibility

These examples are compatible with `pySigma >= 0.11.0`.
