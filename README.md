# drawlist
A draw-list system & gui for rendering to Unreal Engine's Canvas inspired by ImGui.

# Example Usage
```c++
Canvas::NewFrame(canvas); // Create a new frame passing in your canvas

Canvas::DrawList drawList; // Create a drawlist that you manage. You can clear this at anytime with DrawList::Clear();
drawList->AddText(L"Hello", { 500, 500 }, true, FLinearColor(1.0f, 1.0f, 1.0f, 1.0f), Canvas::TextEffect::OUTLINE, Canvas::TextFont::POPPINS_MEDIUM); // Add text to the drawlist
static bool draw_text = false;
Canvas::StartWindow(L"Example Window", { 1000, 500 }); // Initialize the window with a title of 'Example Window'

if (Canvas::Button(L"Click me!")) { draw_text != draw_text }; // Draw a button that if clicked, toggles draw_text.
if (draw_text)
{
    Canvas::Text("You clicked the button!", Canvas::Color::White, Canvas::GetFont(ENGINE_ROBOTO_SMALL)); // Draw text with small roboto font in white if button clicked
}

Canvas::EndAndDrawWindow(drawList); // Draw window to created drawlist. Canvas::EndWindow will draw to persistent drawlist.

Canvas::GetGlobalDrawlist()->AddLine({ 0, 0 }, { 1920, 1080 }, 5, FLinearColor(1.0f, 1.0f, 1.0f, 1.0f)); // Render a white 5 pixel thick line from top-left to bottom-right to the global draw list.


Canvas::RenderDrawList(drawList); // Render the given drawlist.
Canvas::RenderDrawList(Canvas::GetGlobalDrawlist()); // Render the global drawlist
Canvas::EndFrame();
```


