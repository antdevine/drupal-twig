# drupal-twig


Drupal 8 Twig

Example directory link
<script src="/{{ base_path ~ directory }}/media/js/libs/jsfile.js"></script>

Background image
style="background-image: url( '{{ file_url(node.field_background_image_example.entity.fileuri) }}' );"

Text in a tag trimmed white space down
<h2>{{ content.field_animated_blocks_title|render|trim }}</h2>

WYSIWYG Content area
{{ content.field_animated_blocks }}

Paragraph if statement.  If user selects left from the dropdown list then display the code in the statement
{% if paragraph.field_animated_block_img_alignme.value == 'left' %}
{% endif %}

Paragraph enter content, this one was for a drop down list but can be used for other text fields.  This can be added onto a div to output a class as well.
{{paragraph.field_image_animate_type.value}}

Paragraph image link
<img src="{{ file_url(paragraph.field_animated_block_image.entity.fileuri) }}" />

Paragraph content area with extra white space trimmed out
{{ paragraph.field_animated_block_description.value|raw }}

Paragraph set styles.  This sets the styles variable to blank, then if the paragraph.field_background_image.value is not empty it adds the background image to the styles variable, the valiable is then outputted in the div tag.
{% set styles = '' %}
{% if paragraph.field_background_image.value is not empty %}
    {% set styles = ' style="background-image: url( \'' ~ file_url( paragraph.field_background_image.entity.uri.value ) ~ '\' );"' %}
{% endif %}

<div class="backgroundimage__container--img"  {{ styles|raw }}></div>

Paragraph checks if there is content to output before outputting a div with blank content.
{% if paragraph.field_background_image_text.value is not empty %}
                    <div class="backgroundimage__container--txt">
                        {{ paragraph.field_background_image_text.value|raw }}                    
                    </div>
{% endif %}

Node checks if there is content to output before outputting a div with blank content
{% if node.field_application_being_accepted.value is not empty %}
                        <div class="applicationsacceptedbut">
                            <a href="{{ content.field_application_accepted_link.0['#url'] }}"><img src="{{ file_url(node.field_application_being_accepted.entity.fileuri) }}" alt="applications being accepted" /></a>
                        </div>
{% endif %}

Node outputting content/ WYSIWYG content
{{ content.field_banner_with_text_and_butto }}

Paragraph link
<a href="{{ paragraph.field_banner_button_link.0.url }}"></a>

Node setting classes
{% if node.field_callout_strip_icon_amount.value is not empty %}
    {% set classes = classes ~ " " ~ node.field_callout_strip_icon_amount.value %}
{% endif %}

<div class="calloutstripicontext__container {{ classes }}"></div>

Another Example with padding top
{% if node.field_content_area_btn_pddingtop.value is not empty %}
    {% set paddingtop = paddingtop ~ " " ~ node.field_content_area_btn_pddingtop.value %}
{% endif %}

<div style="padding-top:{{ paddingtop|raw }}%;"></div>

Node background image
<div class="slide" style="background-image: url( '{{ file_url( item.content['#item'].entity.uri.value ) }}' );"></div>

Paragraph if statement with an or
{% if paragraph.field_carousel_with_title_title.value is not empty or paragraph.field_carousel_with_title_text.value is not empty %}
        <div>
            {% if paragraph.field_carousel_with_title_title.value %}
                <h2>{{ paragraph.field_carousel_with_title_title.value }}</h2>
            {% endif %}
            {% if paragraph.field_carousel_with_title_text.value %}
                <h3>{{ paragraph.field_carousel_with_title_text.value }}</h3>
            {% endif %}
        </div>
{% endif %}


Node if more than 0 items
{% if node.field_panels_key.getvalue|length > 0 %}
                <ul class="panel-key">{{ content.field_panels_key }}</ul>
{% endif %}

