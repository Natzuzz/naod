
gamelist = {
    2753915549,
    4442272183,
    7449423635
}

spawn(function()-----anti wrong game
    if table.find(gamelist,game.PlaceId) then
    else
        game.Players.localPlayer:Kick('NO GAME')
    end
end)





local StarterGui = game:GetService("StarterGui")
StarterGui:SetCore("SendNotification", {
    Title = "Nao Hub";
    Text = "Welcome To Nao";
    Icon = "rbxassetid://10258071211";
})









local placeId = game.PlaceId
if placeId == 2753915549 then
    world1 = true
elseif placeId == 4442272183 then
    world2 = true
elseif placeId == 7449423635 then
    world3 = true
end


for i,v in pairs(getconnections(game:GetService("Players").localPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton.MouseButton1Click)) do
    v.Function()
end



do
	local ui = game.CoreGui:FindFirstChild("ABc")
	if ui then
		ui:Destroy()
	end
end

local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local LocalPlayer = game:GetService("Players").LocalPlayer
local Mouse = LocalPlayer:GetMouse()
local tween = game:GetService("TweenService")
local Red = {RainbowColorValue = 0, HueSelectionPosition = 0}


local function MakeDraggable(topbarobject, object)
	local Dragging = nil
	local DragInput = nil
	local DragStart = nil
	local StartPosition = nil

	local function Update(input)
		local Delta = input.Position - DragStart
		local pos =
			UDim2.new(
				StartPosition.X.Scale,
				StartPosition.X.Offset + Delta.X,
				StartPosition.Y.Scale,
				StartPosition.Y.Offset + Delta.Y
			)
		local Tween = TweenService:Create(object, TweenInfo.new(0.2), {Position = pos})
		Tween:Play()
	end

	topbarobject.InputBegan:Connect(
		function(input)
			if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
				Dragging = true
				DragStart = input.Position
				StartPosition = object.Position

				input.Changed:Connect(
					function()
						if input.UserInputState == Enum.UserInputState.End then
							Dragging = false
						end
					end
				)
			end
		end
	)

	topbarobject.InputChanged:Connect(
		function(input)
			if
				input.UserInputType == Enum.UserInputType.MouseMovement or
				input.UserInputType == Enum.UserInputType.Touch
			then
				DragInput = input
			end
		end
	)

	UserInputService.InputChanged:Connect(
		function(input)
			if input == DragInput and Dragging then
				Update(input)
			end
		end
	)
end

local function Tween(instance, properties,style,wa)
	if style == nil or "" then
		return Back
	end
	tween:Create(instance,TweenInfo.new(wa,Enum.EasingStyle[style]),{properties}):Play()
end

local ActualTypes = {
	RoundFrame = "ImageLabel",
	Shadow = "ImageLabel",
	Circle = "ImageLabel",
	CircleButton = "ImageButton",
	Frame = "Frame",
	Label = "TextLabel",
	Button = "TextButton",
	SmoothButton = "ImageButton",
	Box = "TextBox",
	ScrollingFrame = "ScrollingFrame",
	Menu = "ImageButton",
	NavBar = "ImageButton"
}

local Properties = {
	RoundFrame = {
		BackgroundTransparency = 1,
		Image = "http://www.roblox.com/asset/?id=5554237731",
		ScaleType = Enum.ScaleType.Slice,
		SliceCenter = Rect.new(3,3,297,297)
	},
	SmoothButton = {
		AutoButtonColor = false,
		BackgroundTransparency = 1,
		Image = "http://www.roblox.com/asset/?id=5554237731",
		ScaleType = Enum.ScaleType.Slice,
		SliceCenter = Rect.new(3,3,297,297)
	},
	Shadow = {
		Name = "Shadow",
		BackgroundTransparency = 1,
		Image = "http://www.roblox.com/asset/?id=5554236805",
		ScaleType = Enum.ScaleType.Slice,
		SliceCenter = Rect.new(23,23,277,277),
		Size = UDim2.fromScale(1,1) + UDim2.fromOffset(30,30),
		Position = UDim2.fromOffset(-15,-15)
	},
	Circle = {
		BackgroundTransparency = 1,
		Image = "http://www.roblox.com/asset/?id=5554831670"
	},
	CircleButton = {
		BackgroundTransparency = 1,
		AutoButtonColor = false,
		Image = "http://www.roblox.com/asset/?id=5554831670"
	},
	Frame = {
		BackgroundTransparency = 1,
		BorderSizePixel = 0,
		Size = UDim2.fromScale(1,1)
	},
	Label = {
		BackgroundTransparency = 1,
		Position = UDim2.fromOffset(5,0),
		Size = UDim2.fromScale(1,1) - UDim2.fromOffset(5,0),
		TextSize = 14,
		TextXAlignment = Enum.TextXAlignment.Left
	},
	Button = {
		BackgroundTransparency = 1,
		Position = UDim2.fromOffset(5,0),
		Size = UDim2.fromScale(1,1) - UDim2.fromOffset(5,0),
		TextSize = 14,
		TextXAlignment = Enum.TextXAlignment.Left
	},
	Box = {
		BackgroundTransparency = 1,
		Position = UDim2.fromOffset(5,0),
		Size = UDim2.fromScale(1,1) - UDim2.fromOffset(5,0),
		TextSize = 14,
		TextXAlignment = Enum.TextXAlignment.Left
	},
	ScrollingFrame = {
		BackgroundTransparency = 1,
		ScrollBarThickness = 0,
		CanvasSize = UDim2.fromScale(0,0),
		Size = UDim2.fromScale(1,1)
	},
	Menu = {
		Name = "More",
		AutoButtonColor = false,
		BackgroundTransparency = 1,
		Image = "http://www.roblox.com/asset/?id=5555108481",
		Size = UDim2.fromOffset(20,20),
		Position = UDim2.fromScale(1,0.5) - UDim2.fromOffset(25,10)
	},
	NavBar = {
		Name = "SheetToggle",
		Image = "http://www.roblox.com/asset/?id=5576439039",
		BackgroundTransparency = 1,
		Size = UDim2.fromOffset(20,20),
		Position = UDim2.fromOffset(5,5),
		AutoButtonColor = false
	}
}

local Types = {
	"RoundFrame",
	"Shadow",
	"Circle",
	"CircleButton",
	"Frame",
	"Label",
	"Button",
	"SmoothButton",
	"Box",
	"ScrollingFrame",
	"Menu",
	"NavBar"
}

function FindType(String)
	for _, Type in next, Types do
		if Type:sub(1, #String):lower() == String:lower() then
			return Type
		end
	end
	return false
end

local Objects = {}

function Objects.new(Type)
	local TargetType = FindType(Type)
	if TargetType then
		local NewImage = Instance.new(ActualTypes[TargetType])
		if Properties[TargetType] then
			for Property, Value in next, Properties[TargetType] do
				NewImage[Property] = Value
			end
		end
		return NewImage
	else
		return Instance.new(Type)
	end
end

local function GetXY(GuiObject)
	local Max, May = GuiObject.AbsoluteSize.X, GuiObject.AbsoluteSize.Y
	local Px, Py = math.clamp(Mouse.X - GuiObject.AbsolutePosition.X, 0, Max), math.clamp(Mouse.Y - GuiObject.AbsolutePosition.Y, 0, May)
	return Px/Max, Py/May
end

local function CircleAnim(GuiObject, EndColour, StartColour)
	local PX, PY = GetXY(GuiObject)
	local Circle = Objects.new("Circle")
	Circle.Size = UDim2.fromScale(0,0)
	Circle.Position = UDim2.fromScale(PX,PY)
	Circle.ImageColor3 = StartColour or GuiObject.ImageColor3
	Circle.ZIndex = 200
	Circle.Parent = GuiObject
	local Size = GuiObject.AbsoluteSize.X
	TweenService:Create(Circle, TweenInfo.new(0.5), {Position = UDim2.fromScale(PX,PY) - UDim2.fromOffset(Size/2,Size/2), ImageTransparency = 1, ImageColor3 = EndColour, Size = UDim2.fromOffset(Size,Size)}):Play()
	spawn(function()
		wait(0.5)
		Circle:Destroy()
	end)
end
local library = {}

function library:Window(text,logo,keybind)
	local uihide = false
	local abc = false
	local logo = logo or 0
	local currentpage = ""
	local keybind = keybind or Enum.KeyCode.RightControl
	local yoo = string.gsub(tostring(keybind),"Enum.KeyCode.","")
	
	local ABc = Instance.new("ScreenGui")
	ABc.Name = "ABc"
	ABc.Parent = game.CoreGui
	ABc.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

	local Main = Instance.new("Frame")
	Main.Name = "Main"
	Main.Parent = ABc
	Main.ClipsDescendants = true
	Main.AnchorPoint = Vector2.new(0.5,0.5)
	Main.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
	Main.Position = UDim2.new(0.5, 0, 0.5, 0)
	Main.Size = UDim2.new(0, 0, 0, 0)
	
	Main:TweenSize(UDim2.new(0, 656, 0, 400),"Out","Quad",0.4,true)

	local MCNR = Instance.new("UICorner")
	MCNR.Name = "MCNR"
	MCNR.Parent = Main

	local Top = Instance.new("Frame")
	Top.Name = "Top"
	Top.Parent = Main
	Top.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
	Top.Size = UDim2.new(0, 656, 0, 27)

	local TCNR = Instance.new("UICorner")
	TCNR.Name = "TCNR"
	TCNR.Parent = Top

	local Logo = Instance.new("ImageLabel")
	Logo.Name = "Logo"
	Logo.Parent = Top
	Logo.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Logo.BackgroundTransparency = 1.000
	Logo.Position = UDim2.new(0, 10, 0, 1)
	Logo.Size = UDim2.new(0, 25, 0, 25)
	Logo.Image = "rbxassetid://"..tostring(logo)

	local Name = Instance.new("TextLabel")
	Name.Name = "Name"
	Name.Parent = Top
	Name.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Name.BackgroundTransparency = 1.000
	Name.Position = UDim2.new(0.0609756112, 0, 0, 0)
	Name.Size = UDim2.new(0, 61, 0, 27)
	Name.Font = Enum.Font.GothamSemibold
	Name.Text = text
	Name.TextColor3 = Color3.fromRGB(225, 225, 225)
	Name.TextSize = 17.000

	local Hub = Instance.new("TextLabel")
	Hub.Name = "Hub"
	Hub.Parent = Top
	Hub.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Hub.BackgroundTransparency = 1.000
	Hub.Position = UDim2.new(0, 90, 0, 0)
	Hub.Size = UDim2.new(0, 81, 0, 27)
	Hub.Font = Enum.Font.GothamSemibold
	Hub.Text = "HUB"
	Hub.TextColor3 = Color3.fromRGB(0, 128, 255)
	Hub.TextSize = 17.000
	Hub.TextXAlignment = Enum.TextXAlignment.Left

	local BindButton = Instance.new("TextButton")
	BindButton.Name = "BindButton"
	BindButton.Parent = Top
	BindButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	BindButton.BackgroundTransparency = 1.000
	BindButton.Position = UDim2.new(0.847561002, 0, 0, 0)
	BindButton.Size = UDim2.new(0, 100, 0, 27)
	BindButton.Font = Enum.Font.GothamSemibold
	BindButton.Text = "[ "..string.gsub(tostring(keybind),"Enum.KeyCode.","").." ]"
	BindButton.TextColor3 = Color3.fromRGB(100, 100, 100)
	BindButton.TextSize = 11.000
	
	BindButton.MouseButton1Click:Connect(function ()
		BindButton.Text = "[ ... ]"
		local inputwait = game:GetService("UserInputService").InputBegan:wait()
		local shiba = inputwait.KeyCode == Enum.KeyCode.Unknown and inputwait.UserInputType or inputwait.KeyCode

		if shiba.Name ~= "Focus" and shiba.Name ~= "MouseMovement" then
			BindButton.Text = "[ "..shiba.Name.." ]"
			yoo = shiba.Name
		end
	end)

	local Tab = Instance.new("Frame")
	Tab.Name = "Tab"
	Tab.Parent = Main
	Tab.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
	Tab.Position = UDim2.new(0, 5, 0, 30)
	Tab.Size = UDim2.new(0, 150, 0, 365)

	local TCNR = Instance.new("UICorner")
	TCNR.Name = "TCNR"
	TCNR.Parent = Tab

	local ScrollTab = Instance.new("ScrollingFrame")
	ScrollTab.Name = "ScrollTab"
	ScrollTab.Parent = Tab
	ScrollTab.Active = true
	ScrollTab.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	ScrollTab.BackgroundTransparency = 1.000
	ScrollTab.Size = UDim2.new(0, 150, 0, 365)
	ScrollTab.CanvasSize = UDim2.new(0, 0, 0, 0)
	ScrollTab.ScrollBarThickness = 0

	local PLL = Instance.new("UIListLayout")
	PLL.Name = "PLL"
	PLL.Parent = ScrollTab
	PLL.SortOrder = Enum.SortOrder.LayoutOrder
	PLL.Padding = UDim.new(0, 15)

	local PPD = Instance.new("UIPadding")
	PPD.Name = "PPD"
	PPD.Parent = ScrollTab
	PPD.PaddingLeft = UDim.new(0, 10)
	PPD.PaddingTop = UDim.new(0, 10)

	local Page = Instance.new("Frame")
	Page.Name = "Page"
	Page.Parent = Main
	Page.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
	Page.Position = UDim2.new(0.245426834, 0, 0.075000003, 0)
	Page.Size = UDim2.new(0, 490, 0, 365)

	local PCNR = Instance.new("UICorner")
	PCNR.Name = "PCNR"
	PCNR.Parent = Page

	local MainPage = Instance.new("Frame")
	MainPage.Name = "MainPage"
	MainPage.Parent = Page
	MainPage.ClipsDescendants = true
	MainPage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	MainPage.BackgroundTransparency = 1.000
	MainPage.Size = UDim2.new(0, 490, 0, 365)

	local PageList = Instance.new("Folder")
	PageList.Name = "PageList"
	PageList.Parent = MainPage

	local UIPageLayout = Instance.new("UIPageLayout")

	UIPageLayout.Parent = PageList
	UIPageLayout.SortOrder = Enum.SortOrder.LayoutOrder
	UIPageLayout.EasingDirection = Enum.EasingDirection.InOut
	UIPageLayout.EasingStyle = Enum.EasingStyle.Quad
	UIPageLayout.FillDirection = Enum.FillDirection.Vertical
	UIPageLayout.Padding = UDim.new(0, 15)
	UIPageLayout.TweenTime = 0.400
	UIPageLayout.GamepadInputEnabled = false
	UIPageLayout.ScrollWheelInputEnabled = false
	UIPageLayout.TouchInputEnabled = false
	
	MakeDraggable(Top,Main)

	do  local ui =  game:GetService("CoreGui"):FindFirstChild("Luna")  if ui then ui:Destroy() end end


	local Luna = Instance.new("ScreenGui")
	local ToggleFrameUi = Instance.new("Frame")
	local UICorner = Instance.new("UICorner")
	local ToggleImgUi = Instance.new("ImageLabel")
	local Uitoggle = Instance.new("TextLabel")
	local Yedhee = Instance.new("TextLabel")
	local SearchStroke = Instance.new("UIStroke")
	
	
	Luna.Name = "Luna"
	Luna.Parent = game.CoreGui
	Luna.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
	
	ToggleFrameUi.Name = "ToggleFrameUi"
	ToggleFrameUi.Parent = Luna
	ToggleFrameUi.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
	ToggleFrameUi.Position = UDim2.new(0.883, 0,0.282, 0)
	ToggleFrameUi.Size = UDim2.new(0, 198, 0, 48)
	
	SearchStroke.Thickness = 1
	SearchStroke.Name = ""
	SearchStroke.Parent = ToggleFrameUi
	SearchStroke.ApplyStrokeMode = Enum.ApplyStrokeMode.Border
	SearchStroke.LineJoinMode = Enum.LineJoinMode.Round
	SearchStroke.Color = Color3.fromRGB(0,128,155)
	SearchStroke.Transparency = 0
	
	UICorner.CornerRadius = UDim.new(0, 4)
	UICorner.Parent = ToggleFrameUi
	
	ToggleImgUi.Name = "ToggleImgUi"
	ToggleImgUi.Parent = ToggleFrameUi
	ToggleImgUi.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	ToggleImgUi.BackgroundTransparency = 1.000
	ToggleImgUi.Position = UDim2.new(0.0454545468, 0, 0.125000313, 0)
	ToggleImgUi.Size = UDim2.new(0, 35, 0, 35)
	ToggleImgUi.Image = "rbxassetid://10268569309"
	
	Uitoggle.Name = "Uitoggle"
	Uitoggle.Parent = ToggleFrameUi
	Uitoggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Uitoggle.BackgroundTransparency = 1.000
	Uitoggle.Position = UDim2.new(0.25757575, 0, 0, 0)
	Uitoggle.Size = UDim2.new(0, 137, 0, 25)
	Uitoggle.Font = Enum.Font.GothamSemibold
	Uitoggle.Text = "Ui Toggle :"
	Uitoggle.TextColor3 = Color3.fromRGB(255, 255, 255)
	Uitoggle.TextSize = 12.000
	
	Yedhee.Name = "Yedhee"
	Yedhee.Parent = ToggleFrameUi
	Yedhee.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
	Yedhee.BackgroundTransparency = 1.000
	Yedhee.Position = UDim2.new(0.25757575, 0, 0.479166657, 0)
	Yedhee.Size = UDim2.new(0, 137, 0, 25)
	Yedhee.Font = Enum.Font.GothamSemibold
	Yedhee.Text = "Lable"
	Yedhee.TextColor3 = Color3.fromRGB(255, 255, 255)
	Yedhee.TextSize = 12.000
	spawn(function()
		while wait() do
			Yedhee.Text = '['..yoo..']'
		end
	end)


	Yedhee.TextTransparency = 1
	Uitoggle.TextTransparency = 1
	ToggleImgUi.ImageTransparency = 1
	ToggleFrameUi.BackgroundTransparency = 1.000
	SearchStroke.Transparency = 1

	UserInputService.InputBegan:Connect(function(input)
		if input.KeyCode == Enum.KeyCode[yoo] then
			if uihide == false then
				game:GetService("TweenService"):Create(
					ToggleFrameUi,
					TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
					{Size = UDim2.new(0, 198, 0, 48)}
				):Play()
				game:GetService("TweenService"):Create(
					ToggleFrameUi,
					TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
					{BackgroundTransparency = 0}
				):Play()
				Yedhee.TextTransparency = 0
				Uitoggle.TextTransparency = 0
				ToggleImgUi.ImageTransparency = 0
				SearchStroke.Transparency = 0
				wait(.2)
				uihide = true
				Main:TweenSize(UDim2.new(0, 0, 0, 0),"In","Quad",0.4,true)
			else
				game:GetService("TweenService"):Create(
					ToggleFrameUi,
					TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
					{Size = UDim2.new(0, 0, 0, 0)}
				):Play()
				game:GetService("TweenService"):Create(
					ToggleFrameUi,
					TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
					{BackgroundTransparency = 1}
				):Play()
				Yedhee.TextTransparency = 1
				Uitoggle.TextTransparency = 1
				ToggleImgUi.ImageTransparency = 1
				SearchStroke.Transparency = 1
				wait(.2)
				uihide = false
				Main:TweenSize(UDim2.new(0, 656, 0, 400),"Out","Quad",0.4,true)
			end
		end
	end)
	MakeDraggable(ToggleFrameUi,ToggleFrameUi)

--[[
	pcall(function()
		game:GetService("UserInputService").InputBegan:Connect(function(io, p)
			if io.KeyCode == Enum.KeyCode[yoo] then
				if uitoggled == false then


					game:GetService("TweenService"):Create(
						ToggleFrameUi,
						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{Size = UDim2.new(0, 0, 0, 0)}
					):Play()
					game:GetService("TweenService"):Create(
						ToggleFrameUi,
						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundTransparency = 1}
					):Play()
					Yedhee.TextTransparency = 1
					Uitoggle.TextTransparency = 1
					ToggleImgUi.ImageTransparency = 1
					wait(.2)
					uitoggled = false
				else
					game:GetService("TweenService"):Create(
						ToggleFrameUi,
						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{Size = UDim2.new(0, 198, 0, 48)}
					):Play()
					game:GetService("TweenService"):Create(
						ToggleFrameUi,
						TweenInfo.new(0.2, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),
						{BackgroundTransparency = 0}
					):Play()
					Yedhee.TextTransparency = 0
					Uitoggle.TextTransparency = 0
					ToggleImgUi.ImageTransparency = 0
					wait(.2)
					uitoggled = true
				end
			end
		end)
	end)
	]]

	local uitab = {}
	
	function uitab:Tab(text)
		local TabButton = Instance.new("TextButton") 
		TabButton.Parent = ScrollTab
		TabButton.Name = text.."Server"
		TabButton.Text = text
		TabButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		TabButton.BackgroundTransparency = 1.000
		TabButton.Size = UDim2.new(0, 130, 0, 23)
		TabButton.Font = Enum.Font.GothamSemibold
		TabButton.TextColor3 = Color3.fromRGB(225, 225, 225)
		TabButton.TextSize = 15.000
		TabButton.TextTransparency = 0.500

		local MainFramePage = Instance.new("ScrollingFrame")
		MainFramePage.Name = text.."_Page"
		MainFramePage.Parent = PageList
		MainFramePage.Active = true
		MainFramePage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		MainFramePage.BackgroundTransparency = 1.000
		MainFramePage.BorderSizePixel = 0
		MainFramePage.Size = UDim2.new(0, 490, 0, 365)
		MainFramePage.CanvasSize = UDim2.new(0, 0, 0, 0)
		MainFramePage.ScrollBarThickness = 0
		
		local UIPadding = Instance.new("UIPadding")
		local UIListLayout = Instance.new("UIListLayout")
		
		UIPadding.Parent = MainFramePage
		UIPadding.PaddingLeft = UDim.new(0, 10)
		UIPadding.PaddingTop = UDim.new(0, 10)

		UIListLayout.Padding = UDim.new(0,15)
		UIListLayout.Parent = MainFramePage
		UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
		
		TabButton.MouseButton1Click:Connect(function()
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0.5}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			for i,v in next, PageList:GetChildren() do
				currentpage = string.gsub(TabButton.Name,"Server","").."_Page"
				if v.Name == currentpage then
					UIPageLayout:JumpTo(v)
				end
			end
		end)

		if abc == false then
			for i,v in next, ScrollTab:GetChildren() do
				if v:IsA("TextButton") then
					TweenService:Create(
						v,
						TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0.5}
					):Play()
				end
				TweenService:Create(
					TabButton,
					TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextTransparency = 0}
				):Play()
			end
			UIPageLayout:JumpToIndex(1)
			abc = true
		end
		
		game:GetService("RunService").Stepped:Connect(function()
			pcall(function()
				MainFramePage.CanvasSize = UDim2.new(0,0,0,UIListLayout.AbsoluteContentSize.Y + 20)
				ScrollTab.CanvasSize = UDim2.new(0,0,0,PLL.AbsoluteContentSize.Y + 20)
			end)
		end)
		
		local main = {}
		function main:Button(text,callback)
			local Button = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
			local TextBtn = Instance.new("TextButton")
			local UICorner_2 = Instance.new("UICorner")
			local Black = Instance.new("Frame")
			local UICorner_3 = Instance.new("UICorner")
			
			Button.Name = "Button"
			Button.Parent = MainFramePage
			Button.BackgroundColor3 = Color3.fromRGB(0, 128, 255)
			Button.Size = UDim2.new(0, 470, 0, 39)
			
			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = Button
			
			TextBtn.Name = "TextBtn"
			TextBtn.Parent = Button
			TextBtn.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			TextBtn.Position = UDim2.new(0, 1, 0, 1)
			TextBtn.Size = UDim2.new(0, 468, 0, 37)
			TextBtn.AutoButtonColor = false
			TextBtn.Font = Enum.Font.GothamSemibold
			TextBtn.Text = text
			TextBtn.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextBtn.TextSize = 15.000
			TextBtn.ClipsDescendants = true
			
			UICorner_2.CornerRadius = UDim.new(0, 5)
			UICorner_2.Parent = TextBtn
			
			Black.Name = "Black"
			Black.Parent = Button
			Black.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
			Black.BackgroundTransparency = 1.000
			Black.BorderSizePixel = 0
			Black.Position = UDim2.new(0, 1, 0, 1)
			Black.Size = UDim2.new(0, 468, 0, 37)
			
			UICorner_3.CornerRadius = UDim.new(0, 5)
			UICorner_3.Parent = Black

			TextBtn.MouseEnter:Connect(function()
				TweenService:Create(
					Black,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundTransparency = 0.7}
				):Play()
			end)
			TextBtn.MouseLeave:Connect(function()
				TweenService:Create(
					Black,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundTransparency = 1}
				):Play()
			end)
			TextBtn.MouseButton1Click:Connect(function()
			    CircleAnim(TextBtn, Color3.fromRGB(255,255,255), Color3.fromRGB(255,255,255))
				TextBtn.TextSize = 0
				TweenService:Create(
					TextBtn,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{TextSize = 15}
				):Play()
				callback()
			end)
		end
		function main:Toggle(text,config,Imgidicon,callback)
			config = config or false
			local toggled = config
			local Toggle = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
			local Button = Instance.new("TextButton")
			local UICorner_2 = Instance.new("UICorner")
			local Label = Instance.new("TextLabel")
			local ToggleImage = Instance.new("Frame")
			local UICorner_3 = Instance.new("UICorner")
			local Circle = Instance.new("Frame")
			local UICorner_4 = Instance.new("UICorner")
            local imgLabelIcon = Instance.new("ImageLabel") --http://www.roblox.com/asset/?id=
            local Circle1 = Instance.new("Frame")

			Toggle.Name = "Toggle"
			Toggle.Parent = MainFramePage
			Toggle.BackgroundColor3 = Color3.fromRGB(0, 128, 255)
			Toggle.Size = UDim2.new(0, 470, 0, 39)

			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = Toggle

			Button.Name = "Button"
			Button.Parent = Toggle
			Button.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			Button.Position = UDim2.new(0, 1, 0, 1)
			Button.Size = UDim2.new(0, 468, 0, 37)
			Button.AutoButtonColor = false
			Button.Font = Enum.Font.SourceSans
			Button.Text = ""
			Button.TextColor3 = Color3.fromRGB(0, 0, 0)
			Button.TextSize = 11.000

			UICorner_2.CornerRadius = UDim.new(0, 5)
			UICorner_2.Parent = Button

			Label.Name = "Label"
			Label.Parent = Toggle
			Label.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Label.BackgroundTransparency = 1.000
			Label.Position = UDim2.new(0, 1, 0, 1)
			Label.Size = UDim2.new(0, 468, 0, 37)
			Label.Font = Enum.Font.GothamSemibold
			Label.Text = text
			Label.TextColor3 = Color3.fromRGB(225, 225, 225)
			Label.TextSize = 15.000

			ToggleImage.Name = "ToggleImage"
			ToggleImage.Parent = Toggle
			ToggleImage.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
			ToggleImage.Position = UDim2.new(0, 415, 0, 10)
			ToggleImage.Size = UDim2.new(0, 45, 0, 20)

			UICorner_3.CornerRadius = UDim.new(0, 10)
			UICorner_3.Parent = ToggleImage

			Circle.Name = "Circle"
			Circle.Parent = ToggleImage
			Circle.BackgroundColor3 = Color3.fromRGB(227, 60, 60)
			Circle.Position = UDim2.new(0, 2, 0, 2)
			Circle.Size = UDim2.new(0, 16, 0, 16)
--[[
			Circle1.Name = "Circle"
			Circle1.Parent = Toggle
			Circle1.BackgroundColor3 = Color3.fromRGB(227, 60, 60)
			Circle1.Position = UDim2.new(0, 10, 0, 9)
			Circle1.Size = UDim2.new(0, 20, 0, 20)]]

            imgLabelIcon.Name = "Icon"
            imgLabelIcon.Parent = Toggle
            imgLabelIcon.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
            imgLabelIcon.BackgroundTransparency = 1.000
            imgLabelIcon.Position = UDim2.new(0, 10, 0, 9)
            imgLabelIcon.Size = UDim2.new(0, 20, 0, 20)
            imgLabelIcon.Image = "http://www.roblox.com/asset/?id="..Imgidicon

			UICorner_4.CornerRadius = UDim.new(0, 10)
			UICorner_4.Parent = Circle

			Button.MouseButton1Click:Connect(function()
				if toggled == false then
					toggled = true
					Circle:TweenPosition(UDim2.new(0,27,0,2),"Out","Sine",0.3,true)
                    TweenService:Create(
						Toggle,
						TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(0, 128, 255)}
					):Play()
					TweenService:Create(
						Circle,
						TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(227, 60, 60)}
					):Play()
				else
					toggled = false
					Circle:TweenPosition(UDim2.new(0,2,0,2),"Out","Sine",0.3,true)
                    TweenService:Create(
						Toggle,
						TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(0, 128, 255)}
					):Play()
					TweenService:Create(
						Circle,
						TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{BackgroundColor3 = Color3.fromRGB(227, 60, 60)}
					):Play()
				end 
				pcall(callback,toggled)
			end)

			if config == true then
				toggled = true
				Circle:TweenPosition(UDim2.new(0,27,0,2),"Out","Sine",0.4,true)
                TweenService:Create(
                    Toggle,
                    TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
                    {BackgroundColor3 = Color3.fromRGB(158, 107, 209)}
                ):Play()
				TweenService:Create(
					Circle,
					TweenInfo.new(0.4,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{BackgroundColor3 = Color3.fromRGB(110,60,227)}
				):Play()
				pcall(callback,toggled)
			end
		end
		function main:Dropdown(text,option,callback)
			local isdropping = false
			local Dropdown = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
			local DropTitle = Instance.new("TextLabel")
			local DropScroll = Instance.new("ScrollingFrame")
			local UIListLayout = Instance.new("UIListLayout")
			local UIPadding = Instance.new("UIPadding")
			local DropButton = Instance.new("TextButton")
			local DropImage = Instance.new("ImageLabel")
			
			Dropdown.Name = "Dropdown"
			Dropdown.Parent = MainFramePage
			Dropdown.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			Dropdown.ClipsDescendants = true
			Dropdown.Size = UDim2.new(0, 470, 0, 39)
			
			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = Dropdown
			
			DropTitle.Name = "DropTitle"
			DropTitle.Parent = Dropdown
			DropTitle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			DropTitle.BackgroundTransparency = 1.000
			DropTitle.Size = UDim2.new(0, 470, 0, 37)
			DropTitle.Font = Enum.Font.GothamSemibold
			DropTitle.Text = text.. " : "
			DropTitle.TextColor3 = Color3.fromRGB(225, 225, 225)
			DropTitle.TextSize = 15.000
			
			DropScroll.Name = "DropScroll"
			DropScroll.Parent = DropTitle
			DropScroll.Active = true
			DropScroll.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			DropScroll.BackgroundTransparency = 1.000
			DropScroll.BorderSizePixel = 0
			DropScroll.Position = UDim2.new(0, 0, 0, 37)
			DropScroll.Size = UDim2.new(0, 470, 0, 100)
			DropScroll.CanvasSize = UDim2.new(0, 0, 0, 0)
			DropScroll.ScrollBarThickness = 3
			
			UIListLayout.Parent = DropScroll
			UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
			UIListLayout.Padding = UDim.new(0, 5)
			
			UIPadding.Parent = DropScroll
			UIPadding.PaddingLeft = UDim.new(0, 5)
			UIPadding.PaddingTop = UDim.new(0, 5)
			
			DropImage.Name = "DropImage"
			DropImage.Parent = Dropdown
			DropImage.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			DropImage.BackgroundTransparency = 1.000
			DropImage.Position = UDim2.new(0, 430, 0, 5.25)
			DropImage.Rotation = 360.000
			DropImage.Size = UDim2.new(0, 30, 0, 30)
			DropImage.Image = "rbxassetid://4370337241"
			
			DropButton.Name = "DropButton"
			DropButton.Parent = Dropdown
			DropButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			DropButton.BackgroundTransparency = 1.000
			DropButton.Size = UDim2.new(0, 470, 0, 37)
			DropButton.Font = Enum.Font.SourceSans
			DropButton.Text = ""
			DropButton.TextColor3 = Color3.fromRGB(0, 0, 0)
			DropButton.TextSize = 14.000

			for i,v in next,option do
				local Item = Instance.new("TextButton")

				Item.Name = "Item"
				Item.Parent = DropScroll
				Item.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Item.BackgroundTransparency = 1.000
				Item.Size = UDim2.new(0, 460, 0, 26)
				Item.Font = Enum.Font.GothamSemibold
				Item.Text = tostring(v)
				Item.TextColor3 = Color3.fromRGB(225, 225, 225)
				Item.TextSize = 13.000
				Item.TextTransparency = 0.500

				Item.MouseEnter:Connect(function()
					TweenService:Create(
						Item,
						TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end)

				Item.MouseLeave:Connect(function()
					TweenService:Create(
						Item,
						TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0.5}
					):Play()
				end)

				Item.MouseButton1Click:Connect(function()
					isdropping = false
					Dropdown:TweenSize(UDim2.new(0,470,0,37),"Out","Quad",0.5,true)
					TweenService:Create(
						DropImage,
						TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{Rotation = 360}
					):Play()
					callback(Item.Text)
					DropTitle.Text = text.." : "..Item.Text
				end)
			end

			DropScroll.CanvasSize = UDim2.new(0,0,0,UIListLayout.AbsoluteContentSize.Y + 10)

			DropButton.MouseButton1Click:Connect(function()
				if isdropping == false then
					isdropping = true
					Dropdown:TweenSize(UDim2.new(0,470,0,131),"Out","Quad",0.5,true)
					TweenService:Create(
						DropImage,
						TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{Rotation = 540}
					):Play()
				else
					isdropping = false
					Dropdown:TweenSize(UDim2.new(0,470,0,37),"Out","Quad",0.5,true)
					TweenService:Create(
						DropImage,
						TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{Rotation = 360}
					):Play()
				end
			end)

			local dropfunc = {}
			function dropfunc:Add(t)
				local Item = Instance.new("TextButton")
				Item.Name = "Item"
				Item.Parent = DropScroll
				Item.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
				Item.BackgroundTransparency = 1.000
				Item.Size = UDim2.new(0, 470, 0, 26)
				Item.Font = Enum.Font.GothamSemibold
				Item.Text = tostring(t)
				Item.TextColor3 = Color3.fromRGB(225, 225, 225)
				Item.TextSize = 13.000
				Item.TextTransparency = 0.500

				Item.MouseEnter:Connect(function()
					TweenService:Create(
						Item,
						TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0}
					):Play()
				end)

				Item.MouseLeave:Connect(function()
					TweenService:Create(
						Item,
						TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{TextTransparency = 0.5}
					):Play()
				end)

				Item.MouseButton1Click:Connect(function()
					isdropping = false
					Dropdown:TweenSize(UDim2.new(0,470,0,37),"Out","Quad",0.5,true)
					TweenService:Create(
						DropImage,
						TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
						{Rotation = 360}
					):Play()
					callback(Item.Text)
					DropTitle.Text = text.." : "..Item.Text
				end)
			end
			function dropfunc:Clear()
				DropTitle.Text = tostring(text).." : "
				isdropping = false
				Dropdown:TweenSize(UDim2.new(0,470,0,37),"Out","Quad",0.5,true)
				TweenService:Create(
					DropImage,
					TweenInfo.new(0.5,Enum.EasingStyle.Quad,Enum.EasingDirection.Out),
					{Rotation = 360}
				):Play()
				for i,v in next, DropScroll:GetChildren() do
					if v:IsA("TextButton") then
						v:Destroy()
					end
				end
			end
			return dropfunc
		end

		function main:Slider(text,min,max,set,callback)
			local Slider = Instance.new("Frame")
			local slidercorner = Instance.new("UICorner")
			local sliderr = Instance.new("Frame")
			local sliderrcorner = Instance.new("UICorner")
			local SliderLabel = Instance.new("TextLabel")
			local HAHA = Instance.new("Frame")
			local AHEHE = Instance.new("TextButton")
			local bar = Instance.new("Frame")
			local bar1 = Instance.new("Frame")
			local bar1corner = Instance.new("UICorner")
			local barcorner = Instance.new("UICorner")
			local circlebar = Instance.new("Frame")
			local UICorner = Instance.new("UICorner")
			local slidervalue = Instance.new("Frame")
			local valuecorner = Instance.new("UICorner")
			local TextBox = Instance.new("TextBox")
			local UICorner_2 = Instance.new("UICorner")

			Slider.Name = "Slider"
			Slider.Parent = MainFramePage
			Slider.BackgroundColor3 = Color3.fromRGB(0,128,255)
			Slider.BackgroundTransparency = 0
			Slider.Size = UDim2.new(0, 470, 0, 72)

			slidercorner.CornerRadius = UDim.new(0, 5)
			slidercorner.Name = "slidercorner"
			slidercorner.Parent = Slider

			sliderr.Name = "sliderr"
			sliderr.Parent = Slider
			sliderr.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			sliderr.Position = UDim2.new(0, 1, 0, 1)
			sliderr.Size = UDim2.new(0, 468, 0, 70)

			sliderrcorner.CornerRadius = UDim.new(0, 5)
			sliderrcorner.Name = "sliderrcorner"
			sliderrcorner.Parent = sliderr

			SliderLabel.Name = "SliderLabel"
			SliderLabel.Parent = sliderr
			SliderLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			SliderLabel.BackgroundTransparency = 1.000
			SliderLabel.Position = UDim2.new(0, 15, 0, 3)
			SliderLabel.Size = UDim2.new(0, 360, 0, 26)
			SliderLabel.Font = Enum.Font.GothamSemibold
			SliderLabel.Text = text
			SliderLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
			SliderLabel.TextSize = 16.000
			SliderLabel.TextTransparency = 0
			SliderLabel.TextXAlignment = Enum.TextXAlignment.Left

			HAHA.Name = "HAHA"
			HAHA.Parent = sliderr
			HAHA.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			HAHA.BackgroundTransparency = 1.000
			HAHA.Size = UDim2.new(0, 468, 0, 29)

			AHEHE.Name = "AHEHE"
			AHEHE.Parent = sliderr
			AHEHE.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			AHEHE.BackgroundTransparency = 1.000
			AHEHE.Position = UDim2.new(0, 10, 0, 50)
			AHEHE.Size = UDim2.new(0, 448, 0, 5)
			AHEHE.Font = Enum.Font.SourceSans
			AHEHE.Text = ""
			AHEHE.TextColor3 = Color3.fromRGB(0, 0, 0)
			AHEHE.TextSize = 14.000

			bar.Name = "bar"
			bar.Parent = AHEHE
			bar.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
			bar.Size = UDim2.new(0, 448, 0, 5)

			bar1.Name = "bar1"
			bar1.Parent = bar
			bar1.BackgroundColor3 = Color3.fromRGB(0,128,255)
			bar1.BackgroundTransparency = 0
			bar1.Size = UDim2.new(set/max, 0, 0, 5)

			bar1corner.CornerRadius = UDim.new(0, 5)
			bar1corner.Name = "bar1corner"
			bar1corner.Parent = bar1

			barcorner.CornerRadius = UDim.new(0, 5)
			barcorner.Name = "barcorner"
			barcorner.Parent = bar

			circlebar.Name = "circlebar"
			circlebar.Parent = bar1
			circlebar.BackgroundColor3 = Color3.fromRGB(225, 225, 225)
			circlebar.Position = UDim2.new(1, -2, 0, -3)
			circlebar.Size = UDim2.new(0, 10, 0, 10)

			UICorner.CornerRadius = UDim.new(0, 100)
			UICorner.Parent = circlebar

			slidervalue.Name = "slidervalue"
			slidervalue.Parent = sliderr
			slidervalue.BackgroundColor3 = Color3.fromRGB(0,128,255)
			slidervalue.BackgroundTransparency = 0
			slidervalue.Position = UDim2.new(0, 395, 0, 7)
			slidervalue.Size = UDim2.new(0, 65, 0, 22)

			valuecorner.CornerRadius = UDim.new(0, 5)
			valuecorner.Name = "valuecorner"
			valuecorner.Parent = slidervalue

			TextBox.Parent = slidervalue
			TextBox.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
			TextBox.Position = UDim2.new(0, 1, 0, 1)
			TextBox.Size = UDim2.new(0, 63, 0, 20)
			TextBox.Font = Enum.Font.GothamSemibold
			TextBox.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextBox.TextSize = 9.000
			TextBox.Text = set
			TextBox.TextTransparency = 0

			UICorner_2.CornerRadius = UDim.new(0, 5)
			UICorner_2.Parent = TextBox

			local mouse = game.Players.LocalPlayer:GetMouse()
			local uis = game:GetService("UserInputService")

			if Value == nil then
				Value = set
				pcall(function()
					callback(Value)
				end)
			end
			
			AHEHE.MouseButton1Down:Connect(function()
				Value = math.floor((((tonumber(max) - tonumber(min)) / 448) * bar1.AbsoluteSize.X) + tonumber(min)) or 0
				pcall(function()
					callback(Value)
				end)
				bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
				circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
				moveconnection = mouse.Move:Connect(function()
					TextBox.Text = Value
					Value = math.floor((((tonumber(max) - tonumber(min)) / 448) * bar1.AbsoluteSize.X) + tonumber(min))
					pcall(function()
						callback(Value)
					end)
					bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
					circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
				end)
				releaseconnection = uis.InputEnded:Connect(function(Mouse)
					if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
						Value = math.floor((((tonumber(max) - tonumber(min)) / 448) * bar1.AbsoluteSize.X) + tonumber(min))
						pcall(function()
							callback(Value)
						end)
						bar1.Size = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X, 0, 448), 0, 5)
						circlebar.Position = UDim2.new(0, math.clamp(mouse.X - bar1.AbsolutePosition.X - 2, 0, 438), 0, -3)
						moveconnection:Disconnect()
						releaseconnection:Disconnect()
					end
				end)
			end)
			releaseconnection = uis.InputEnded:Connect(function(Mouse)
				if Mouse.UserInputType == Enum.UserInputType.MouseButton1 then
					Value = math.floor((((tonumber(max) - tonumber(min)) / 448) * bar1.AbsoluteSize.X) + tonumber(min))
					TextBox.Text = Value
				end
			end)

			TextBox.FocusLost:Connect(function()
				if tonumber(TextBox.Text) > max then
					TextBox.Text  = max
				end
				bar1.Size = UDim2.new((TextBox.Text or 0) / max, 0, 0, 5)
				circlebar.Position = UDim2.new(1, -2, 0, -3)
				TextBox.Text = tostring(TextBox.Text and math.floor( (TextBox.Text / max) * (max - min) + min) )
				pcall(callback, TextBox.Text)
			end)
		end

		function main:Textbox(text,disappear,callback)
			local Textbox = Instance.new("Frame")
			local TextboxCorner = Instance.new("UICorner")
			local Textboxx = Instance.new("Frame")
			local TextboxxCorner = Instance.new("UICorner")
			local TextboxLabel = Instance.new("TextLabel")
			local txtbtn = Instance.new("TextButton")
			local RealTextbox = Instance.new("TextBox")
			local UICorner = Instance.new("UICorner")

			Textbox.Name = "Textbox"
			Textbox.Parent = MainFramePage
			Textbox.BackgroundColor3 = Color3.fromRGB(0,128,255)
			Textbox.BackgroundTransparency = 0
			Textbox.Size = UDim2.new(0, 470, 0, 39)

			TextboxCorner.CornerRadius = UDim.new(0, 5)
			TextboxCorner.Name = "TextboxCorner"
			TextboxCorner.Parent = Textbox

			Textboxx.Name = "Textboxx"
			Textboxx.Parent = Textbox
			Textboxx.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
			Textboxx.Position = UDim2.new(0, 1, 0, 1)
			Textboxx.Size = UDim2.new(0, 468, 0, 37)

			TextboxxCorner.CornerRadius = UDim.new(0, 5)
			TextboxxCorner.Name = "TextboxxCorner"
			TextboxxCorner.Parent = Textboxx

			TextboxLabel.Name = "TextboxLabel"
			TextboxLabel.Parent = Textbox
			TextboxLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			TextboxLabel.BackgroundTransparency = 1.000
			TextboxLabel.Position = UDim2.new(0, 15, 0, 3)
			TextboxLabel.Text = text
			TextboxLabel.Size = UDim2.new(0, 145, 0, 31)
			TextboxLabel.Font = Enum.Font.GothamSemibold
			TextboxLabel.TextColor3 = Color3.fromRGB(225, 225, 225)
			TextboxLabel.TextSize = 16.000
			TextboxLabel.TextTransparency = 0
			TextboxLabel.TextXAlignment = Enum.TextXAlignment.Left

			txtbtn.Name = "txtbtn"
			txtbtn.Parent = Textbox
			txtbtn.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			txtbtn.BackgroundTransparency = 1.000
			txtbtn.Position = UDim2.new(0, 1, 0, 1)
			txtbtn.Size = UDim2.new(0, 468, 0, 29)
			txtbtn.Font = Enum.Font.SourceSans
			txtbtn.Text = ""
			txtbtn.TextColor3 = Color3.fromRGB(0, 0, 0)
			txtbtn.TextSize = 14.000

			RealTextbox.Name = "RealTextbox"
			RealTextbox.Parent = Textbox
			RealTextbox.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
			RealTextbox.BackgroundTransparency = 0
			RealTextbox.Position = UDim2.new(0, 360, 0, 7)
			RealTextbox.Size = UDim2.new(0, 100, 0, 24)
			RealTextbox.Font = Enum.Font.GothamSemibold
			RealTextbox.Text = ""
			RealTextbox.TextColor3 = Color3.fromRGB(225, 225, 225)
			RealTextbox.TextSize = 11.000
			RealTextbox.TextTransparency = 0

			RealTextbox.FocusLost:Connect(function()
				callback(RealTextbox.Text)
				if disappear then
					RealTextbox.Text = ""
				end
			end)

			UICorner.CornerRadius = UDim.new(0, 5)
			UICorner.Parent = RealTextbox
		end
		function main:Label(text)
			local Label = Instance.new("TextLabel")
			local PaddingLabel = Instance.new("UIPadding")
			local labell = {}
	
			Label.Name = "Label"
			Label.Parent = MainFramePage
			Label.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Label.BackgroundTransparency = 1.000
			Label.Size = UDim2.new(0, 470, 0, 20)
			Label.Font = Enum.Font.GothamSemibold
			Label.TextColor3 = Color3.fromRGB(225, 225, 225)
			Label.TextSize = 16.000
			Label.Text = text
			Label.TextXAlignment = Enum.TextXAlignment.Left

			PaddingLabel.PaddingLeft = UDim.new(0,15)
			PaddingLabel.Parent = Label
			PaddingLabel.Name = "PaddingLabel"
	
			function labell:Set(newtext)
				Label.Text = newtext
			end

			return labell
		end
		function main:Seperator(text)
			local Seperator = Instance.new("Frame")
			local Sep1 = Instance.new("Frame")
			local Sep2 = Instance.new("TextLabel")
			local Sep3 = Instance.new("Frame")
			
			Seperator.Name = "Seperator"
			Seperator.Parent = MainFramePage
			Seperator.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Seperator.BackgroundTransparency = 1.000
			Seperator.Size = UDim2.new(0, 470, 0, 20)
			
			Sep1.Name = "Sep1"
			Sep1.Parent = Seperator
			Sep1.BackgroundColor3 = Color3.fromRGB(173, 121, 226)
			Sep1.BorderSizePixel = 0
			Sep1.Position = UDim2.new(0, 0, 0, 10)
			Sep1.Size = UDim2.new(0, 80, 0, 1)
			
			Sep2.Name = "Sep2"
			Sep2.Parent = Seperator
			Sep2.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Sep2.BackgroundTransparency = 1.000
			Sep2.Position = UDim2.new(0, 185, 0, 0)
			Sep2.Size = UDim2.new(0, 100, 0, 20)
			Sep2.Font = Enum.Font.GothamSemibold
			Sep2.Text = text
			Sep2.TextColor3 = Color3.fromRGB(255, 255, 255)
			Sep2.TextSize = 14.000
			
			Sep3.Name = "Sep3"
			Sep3.Parent = Seperator
			Sep3.BackgroundColor3 = Color3.fromRGB(173, 121, 226)
			Sep3.BorderSizePixel = 0
			Sep3.Position = UDim2.new(0, 390, 0, 10)
			Sep3.Size = UDim2.new(0, 80, 0, 1)
		end

		function main:Line()
			local Linee = Instance.new("Frame")
			local Line = Instance.new("Frame")
			
			Linee.Name = "Linee"
			Linee.Parent = MainFramePage
			Linee.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
			Linee.BackgroundTransparency = 1.000
			Linee.Position = UDim2.new(0, 0, 0.119999997, 0)
			Linee.Size = UDim2.new(0, 470, 0, 20)
			
			Line.Name = "Line"
			Line.Parent = Linee
			Line.BackgroundColor3 = Color3.fromRGB(0,128,255)
			Line.BorderSizePixel = 0
			Line.Position = UDim2.new(0, 0, 0, 10)
			Line.Size = UDim2.new(0, 470, 0, 1)
		end
		return main
	end
	return uitab
end

local win = library:Window("Nao","10268569309",Enum.KeyCode.RightControl)

local AutoFarmTab = win:Tab("Main")


function TP(P)
	Distance = (P.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
	if Distance < 10 then
		Speed = 1000
	elseif Distance < 170 then
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = P
		Speed = 350
	elseif Distance < 1000 then
		Speed = 350
	elseif Distance >= 1000 then
		Speed = 250
	end
	game:GetService("TweenService"):Create(
		game.Players.LocalPlayer.Character.HumanoidRootPart,
		TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
		{CFrame = P}
	):Play()
end


AutoFarmTab:Toggle("Auto Fram",false,"6022668898",function(x)
	_G.Autofram = x
	getgenv().noclip = x
    FarmStat = x
    _TweenCanCel()
end)




AutoFarmTab:Toggle("Super Fast Attack",false,"6022668898",function(x)
	_G.Autofram = x
	getgenv().noclip = x
    FarmStat = x
    _TweenCanCel()
end)

Weapon = {}
for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
    if v:IsA ("Tool") then
        table.insert(Weapon,v.Name)
    end
end


local drop = AutoFarmTab:Dropdown("Select Weapon",Weapon, function(t)
	_G.SelectWeapon = t
 end)

 AutoFarmTab:Button("Refresh Weapon",function()
	drop:Clear()
	for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
		if v:IsA ("Tool") then
			table.insert(Weapon,v.Name)
	drop:Add(v.Name)
			end
		end
	end)


	AutoFarmTab:Line()

reedeemCODE = {"Sub2Fer999","Enyu_is_Pro","Magicbus","JCWK","Starcodeheo","Bluxxy","THEGREATACE","SUB2GAMERROBOT_EXP1","Sub2OfficialNoobie","StrawHatMaine","SUB2NOOBMASTER123","Sub2Daigrock","Axiore","TantaiGaming"}

AutoFarmTab:Button("Redeem all x2 codes",function()
	for r,coderd in pairs(reedeemCODE) do
		pcall(function()
			local args = {
				[1] = coderd
			}
			game:GetService("ReplicatedStorage").Remotes.Redeem:InvokeServer(unpack(args))
		end)
	end    
end)

if world1 then
	AutoFarmTab:Toggle("Auto New World", _G.AutoNewworld,"6022668898", function(vu)
		Auto_Newworld = vu
        _G.AutoHaki = vu
		getgenv().noclip = vu
		UseFast = vu
		if vu == false then
			wait(1)
			TP(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame)
		end
	end)
end


if world1 then
	AutoFarmTab:Toggle("AutoSaber",_G.AutoSaber, "6022668898",function(vu)
		AutoSaber = vu
		UseFast = vu
	getgenv().noclip = vu
	_G.AutoHaki = vu
	end)  
end
	
	
	
	spawn(function()
		while wait(.1) do
			if _G.AutoHaki then 
				if game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
	
				else
					local args = {
						[1] = "Buso"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
			end
		end
	end)

AutoFarmTab:Toggle('Auto Yama',_G.Autoyama,'6022668898',function(value)
	_G.Autoyama = value
	UseFast = value
	getgenv().noclip = value
end)
AutoFarmTab:Toggle('Auto Yama Hop',_G.Autoyama_Hop,'6022668898',function(value)
	_G.Hopsword = value
	UseFast = value
	getgenv().noclip = value
end)
AutoFarmTab:Toggle('Auto Buddy',_G.Buddy,'6022668898',function(value)
	_G.Buddy = value
	getgenv().noclip = value
	UseFast = value
end)
AutoFarmTab:Toggle('Auto Buddy Hop',_G.Buddy_Hop,'6022668898',function(value)
	_G.Hopsword2 = value
	UseFast = value
	getgenv().noclip = value
end)

AutoFarmTab:Toggle('Auto Canvender',_G.Canvender,'6022668898',function(value)
	_G.Canvender = value
	getgenv().noclip = value
	UseFast = value
end	)
AutoFarmTab:Toggle('Auto Canvender Hop',_G.Canvender_Hop,'6022668898',function(value)
	_G.Hopsword3 = value
	getgenv().noclip = value
	UseFast = value
end	)
AutoFarmTab:Toggle('Auto Bone',_G.Auto_Bone,'6022668898',function(value)
	Auto_Bone = value
	getgenv().noclip = value
	UseFast = value
end)

AutoFarmTab:Toggle('Auto Hallow Scythe',_G.Hallow_Scythe,'6022668898',function(value)
	_G.Hallow_Scythe = value
	getgenv().noclip = value
	UseFast = value
end)

AutoFarmTab:Toggle('Auto Drak Dagger',_G.Auto_Dark_Dagger,'6022668898',function(value)
	_G.Auto_Dark_Dagger = value
	getgenv().noclip = value
	UseFast = value
end)
AutoFarmTab:Toggle('Auto Rengoku',_G.Auto_Rengoku,'6022668898',function(value)
	_G.Auto_Rengoku = value
	getgenv().noclip = value
	UseFast = value
end)
AutoFarmTab:Toggle('Auto Rengoku Hop',_G.Auto_Rengoku_Hop,'6022668898',function(value)
	_G.Hopsword4 = value
	getgenv().noclip = value
	UseFast = value
end)
AutoFarmTab:Line()

AutoFarmTab:Dropdown("Select Mode",{'Fruit','Gun'}, function(t)
	_G.SelectMode = t
end)

AutoFarmTab:Toggle('Auto Farm Mas',false,'6022668898',function(value)
	_G.Farm_Mas = value
	getgenv().noclip = value
	UseFast = value
end)
local BossTab = win:Tab("Boss")

local Bosslist = {}
for i, v in pairs(game.ReplicatedStorage:GetChildren()) do
    if string.find(v.Name, "Boss") then
        if v.Name ~= "Ice Admiral [Lv. 700] [Boss]" then
            table.insert(Bosslist, v.Name)
        end
    end
end
for i, v in pairs(game.workspace.Enemies:GetChildren()) do
    if string.find(v.Name, "Boss") then
        if v.Name ~= "Ice Admiral [Lv. 700] [Boss]" then
            table.insert(Bosslist, v.Name)
        end
    end
end
_G.SelectBoss = ""
local BossSelected = BossTab:Dropdown("Select Boss",Bosslist, function(t)
	_G.SelectBoss = t
end)
BossTab:Button("Refresh Boss", function()
	BossSelected:Clear()
	local Boss = {}
	for i, v in pairs(game.ReplicatedStorage:GetChildren()) do
		if string.find(v.Name, "Boss") then
			if v.Name == "Ice Admiral [Lv. 700] [Boss]" then
			else
				table.insert(Bosslist, v.Name)
			end
		end
	end
	for i, v in pairs(game.workspace.Enemies:GetChildren()) do
		if string.find(v.Name, "Boss") then
			if v.Name == "Ice Admiral [Lv. 700] [Boss]" then
			else
				table.insert(Bosslist, v.Name)
			end
		end
	end
end)

BossTab:Toggle('Auto Farm Boss',_G.Farm_Boss,'6022668898',function(value)
	_G.AutoBoss = value
	getgenv().noclip = value
	UseFast = value
end)

Weapon = {}
for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
    if v:IsA ("Tool") then
        table.insert(Weapon,v.Name)
    end
end


local bossw = BossTab:Dropdown("Select Weapon",Weapon, function(t)
	_G.SelectWeaponB = t
 end)

 BossTab:Button("Refresh Weapon",function()
	bossw:Clear()
	for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
		if v:IsA ("Tool") then
			table.insert(Weapon,v.Name)
			bossw:Add(v.Name)
			end
		end
	end)

function CheckQuestBoss()
	-- Old World
	if _G.SelectBoss == "Saber Expert [Lv. 200] [Boss]" then
		MsBoss = "Saber Expert [Lv. 200] [Boss]"
		NameBoss = "Saber Expert"
		CFrameBoss = CFrame.new(-1458.89502, 29.8870335, -50.633564, 0.858821094, 1.13848939e-08, 0.512275636, -4.85649254e-09, 1, -1.40823326e-08, -0.512275636, 9.6063415e-09, 0.858821094)
	elseif _G.SelectBoss == "The Saw [Lv. 100] [Boss]" then
		MsBoss = "The Saw [Lv. 100] [Boss]"
		NameBoss = "The Saw"
		CFrameBoss = CFrame.new(-683.519897, 13.8534927, 1610.87854, -0.290192783, 6.88365773e-08, 0.956968188, 6.98413629e-08, 1, -5.07531119e-08, -0.956968188, 5.21077759e-08, -0.290192783)
	elseif _G.SelectBoss == "Greybeard [Lv. 750] [Raid Boss]" then
		MsBoss = "Greybeard [Lv. 750] [Raid Boss]"
		NameBoss = "Greybeard"
		CFrameBoss = CFrame.new(-4955.72949, 80.8163834, 4305.82666, -0.433646321, -1.03394289e-08, 0.901083171, -3.0443168e-08, 1, -3.17633075e-09, -0.901083171, -2.88092288e-08, -0.433646321)
	elseif _G.SelectBoss == "The Gorilla King [Lv. 25] [Boss]" then
		MsBoss = "The Gorilla King [Lv. 25] [Boss]"
		NameBoss = "The Gorilla King"
		NameQuestBoss = "JungleQuest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-1604.12012, 36.8521118, 154.23732, 0.0648873374, -4.70858913e-06, -0.997892559, 1.41431883e-07, 1, -4.70933674e-06, 0.997892559, 1.64442184e-07, 0.0648873374)
		CFrameBoss = CFrame.new(-1223.52808, 6.27936459, -502.292664, 0.310949147, -5.66602516e-08, 0.950426519, -3.37275488e-08, 1, 7.06501808e-08, -0.950426519, -5.40241736e-08, 0.310949147)
	elseif _G.SelectBoss == "Bobby [Lv. 55] [Boss]" then
		MsBoss = "Bobby [Lv. 55] [Boss]"
		NameBoss = "Bobby"
		NameQuestBoss = "BuggyQuest1"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-1139.59717, 4.75205183, 3825.16211, -0.959730506, -7.5857054e-09, 0.280922383, -4.06310328e-08, 1, -1.11807175e-07, -0.280922383, -1.18718916e-07, -0.959730506)
		CFrameBoss = CFrame.new(-1147.65173, 32.5966301, 4156.02588, 0.956680477, -1.77109952e-10, -0.29113996, 5.16530874e-10, 1, 1.08897802e-09, 0.29113996, -1.19218679e-09, 0.956680477)
	elseif _G.SelectBoss == "Yeti [Lv. 110] [Boss]" then
		MsBoss = "Yeti [Lv. 110] [Boss]"
		NameBoss = "Yeti"
		NameQuestBoss = "SnowQuest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(1384.90247, 87.3078308, -1296.6825, 0.280209213, 2.72035177e-08, -0.959938943, -6.75690828e-08, 1, 8.6151708e-09, 0.959938943, 6.24481444e-08, 0.280209213)
		CFrameBoss = CFrame.new(1221.7356, 138.046906, -1488.84082, 0.349343032, -9.49245944e-08, 0.936994851, 6.29478194e-08, 1, 7.7838429e-08, -0.936994851, 3.17894653e-08, 0.349343032)
	elseif _G.SelectBoss == "Mob Leader [Lv. 120] [Boss]" then
		MsBoss = "Mob Leader [Lv. 120] [Boss]"
		NameBoss = "Mob Leader"
		CFrameBoss = CFrame.new(-2848.59399, 7.4272871, 5342.44043, -0.928248107, -8.7248246e-08, 0.371961564, -7.61816636e-08, 1, 4.44474857e-08, -0.371961564, 1.29216433e-08, -0.92824)
	elseif _G.SelectBoss == "Vice Admiral [Lv. 130] [Boss]" then
		MsBoss = "Vice Admiral [Lv. 130] [Boss]"
		NameBoss = "Vice Admiral"
		NameQuestBoss = "MarineQuest2"
		LevelQuestBoss = 2
		CFrameQuestBoss = CFrame.new(-5035.42285, 28.6520386, 4324.50293, -0.0611100644, -8.08395768e-08, 0.998130739, -1.57416586e-08, 1, 8.00271849e-08, -0.998130739, -1.08217701e-08, -0.0611100644)
		CFrameBoss = CFrame.new(-5078.45898, 99.6520691, 4402.1665, -0.555574954, -9.88630566e-11, 0.831466436, -6.35508286e-08, 1, -4.23449258e-08, -0.831466436, -7.63661632e-08, -0.555574954)
	elseif _G.SelectBoss == "Warden [Lv. 175] [Boss]" then
		MsBoss = "Warden [Lv. 175] [Boss]"
		NameBoss = "Warden"
		NameQuestBoss = "ImpelQuest"
		LevelQuestBoss = 1
		CFrameQuestBoss = CFrame.new(4851.35059, 5.68744135, 743.251282, -0.538484037, -6.68303741e-08, -0.842635691, 1.38001752e-08, 1, -8.81300792e-08, 0.842635691, -5.90851599e-08, -0.538484037)
		CFrameBoss = CFrame.new(5232.5625, 5.26856995, 747.506897, 0.943829298, -4.5439414e-08, 0.330433697, 3.47818627e-08, 1, 3.81658154e-08, -0.330433697, -2.45289105e-08, 0.943829298)
	elseif _G.SelectBoss == "Chief Warden [Lv. 200] [Boss]" then
		MsBoss = "Chief Warden [Lv. 200] [Boss]"
		NameBoss = "Chief Warden"
		NameQuestBoss = "ImpelQuest"
		LevelQuestBoss = 2
		CFrameQuestBoss = CFrame.new(4851.35059, 5.68744135, 743.251282, -0.538484037, -6.68303741e-08, -0.842635691, 1.38001752e-08, 1, -8.81300792e-08, 0.842635691, -5.90851599e-08, -0.538484037)
		CFrameBoss = CFrame.new(5232.5625, 5.26856995, 747.506897, 0.943829298, -4.5439414e-08, 0.330433697, 3.47818627e-08, 1, 3.81658154e-08, -0.330433697, -2.45289105e-08, 0.943829298)
	elseif _G.SelectBoss == "Swan [Lv. 225] [Boss]" then
		MsBoss = "Swan [Lv. 225] [Boss]"
		NameBoss = "Swan"
		NameQuestBoss = "ImpelQuest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(4851.35059, 5.68744135, 743.251282, -0.538484037, -6.68303741e-08, -0.842635691, 1.38001752e-08, 1, -8.81300792e-08, 0.842635691, -5.90851599e-08, -0.538484037)
		CFrameBoss = CFrame.new(5232.5625, 5.26856995, 747.506897, 0.943829298, -4.5439414e-08, 0.330433697, 3.47818627e-08, 1, 3.81658154e-08, -0.330433697, -2.45289105e-08, 0.943829298)
	elseif _G.SelectBoss == "Magma Admiral [Lv. 350] [Boss]" then
		MsBoss = "Magma Admiral [Lv. 350] [Boss]"
		NameBoss = "Magma Admiral"
		NameQuestBoss = "MagmaQuest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-5317.07666, 12.2721891, 8517.41699, 0.51175487, -2.65508806e-08, -0.859131515, -3.91131572e-08, 1, -5.42026761e-08, 0.859131515, 6.13418294e-08, 0.51175487)
		CFrameBoss = CFrame.new(-5530.12646, 22.8769703, 8859.91309, 0.857838571, 2.23414389e-08, 0.513919294, 1.53689133e-08, 1, -6.91265853e-08, -0.513919294, 6.71978384e-08, 0.857838571)
	elseif _G.SelectBoss == "Fishman Lord [Lv. 425] [Boss]" then
		MsBoss = "Fishman Lord [Lv. 425] [Boss]"
		NameBoss = "Fishman Lord"
		NameQuestBoss = "FishmanQuest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(61123.0859, 18.5066795, 1570.18018, 0.927145958, 1.0624845e-07, 0.374700129, -6.98219367e-08, 1, -1.10790765e-07, -0.374700129, 7.65569368e-08, 0.927145958)
		CFrameBoss = CFrame.new(61351.7773, 31.0306778, 1113.31409, 0.999974668, 0, -0.00714713801, 0, 1.00000012, 0, 0.00714714266, 0, 0.999974549)
	elseif _G.SelectBoss == "Wysper [Lv. 500] [Boss]" then
		MsBoss = "Wysper [Lv. 500] [Boss]"
		NameBoss = "Wysper"
		NameQuestBoss = "SkyExp1Quest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-7862.94629, 5545.52832, -379.833954, 0.462944925, 1.45838088e-08, -0.886386991, 1.0534996e-08, 1, 2.19553424e-08, 0.886386991, -1.95022007e-08, 0.462944925)
		CFrameBoss = CFrame.new(-7925.48389, 5550.76074, -636.178345, 0.716468513, -1.22915289e-09, 0.697619379, 3.37381434e-09, 1, -1.70304748e-09, -0.697619379, 3.57381835e-09, 0.716468513)
	elseif _G.SelectBoss == "Thunder God [Lv. 575] [Boss]" then
		MsBoss = "Thunder God [Lv. 575] [Boss]"
		NameBoss = "Thunder God"
		NameQuestBoss = "SkyExp2Quest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-7902.78613, 5635.99902, -1411.98706, -0.0361216255, -1.16895912e-07, 0.999347389, 1.44533963e-09, 1, 1.17024491e-07, -0.999347389, 5.6715117e-09, -0.0361216255)
		CFrameBoss = CFrame.new(-7917.53613, 5616.61377, -2277.78564, 0.965189934, 4.80563429e-08, -0.261550069, -6.73089886e-08, 1, -6.46515304e-08, 0.261550069, 8.00056768e-08, 0.965189934)
	elseif _G.SelectBoss == "Cyborg [Lv. 675] [Boss]" then
		MsBoss = "Cyborg [Lv. 675] [Boss]"
		NameBoss = "Cyborg"
		NameQuestBoss = "FountainQuest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(5253.54834, 38.5361786, 4050.45166, -0.0112687312, -9.93677887e-08, -0.999936521, 2.55291371e-10, 1, -9.93769547e-08, 0.999936521, -1.37512213e-09, -0.0112687312)
		CFrameBoss = CFrame.new(6041.82813, 52.7112198, 3907.45142, -0.563162148, 1.73805248e-09, -0.826346457, -5.94632716e-08, 1, 4.26280238e-08, 0.826346457, 7.31437524e-08, -0.563162148)
	-- New World
	elseif _G.SelectBoss == "Diamond [Lv. 750] [Boss]" then
		MsBoss = "Diamond [Lv. 750] [Boss]"
		NameBoss = "Diamond"
		NameQuestBoss = "Area1Quest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-424.080078, 73.0055847, 1836.91589, 0.253544956, -1.42165932e-08, 0.967323601, -6.00147771e-08, 1, 3.04272909e-08, -0.967323601, -6.5768397e-08, 0.253544956)
		CFrameBoss = CFrame.new(-1736.26587, 198.627731, -236.412857, -0.997808516, 0, -0.0661673471, 0, 1, 0, 0.0661673471, 0, -0.997808516)
	elseif _G.SelectBoss == "Jeremy [Lv. 850] [Boss]" then
		MsBoss = "Jeremy [Lv. 850] [Boss]"
		NameBoss = "Jeremy"
		NameQuestBoss = "Area2Quest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(632.698608, 73.1055908, 918.666321, -0.0319722369, 8.96074881e-10, -0.999488771, 1.36326533e-10, 1, 8.92172336e-10, 0.999488771, -1.07732087e-10, -0.0319722369)
		CFrameBoss = CFrame.new(2203.76953, 448.966034, 752.731079, -0.0217453763, 0, -0.999763548, 0, 1, 0, 0.999763548, 0, -0.0217453763)
	elseif _G.SelectBoss == "Fajita [Lv. 925] [Boss]" then
		MsBoss = "Fajita [Lv. 925] [Boss]"
		NameBoss = "Fajita"
		NameQuestBoss = "MarineQuest3"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-2442.65015, 73.0511475, -3219.11523, -0.873540044, 4.2329841e-08, -0.486752301, 5.64383384e-08, 1, -1.43220786e-08, 0.486752301, -3.99823996e-08, -0.873540044)
		CFrameBoss = CFrame.new(-2297.40332, 115.449463, -3946.53833, 0.961227536, -1.46645796e-09, -0.275756449, -2.3212845e-09, 1, -1.34094433e-08, 0.275756449, 1.35296352e-08, 0.961227536)
	elseif _G.SelectBoss == "Don Swan [Lv. 1000] [Boss]" then
		MsBoss = "Don Swan [Lv. 1000] [Boss]"
		NameBoss = "Don Swan"
		CFrameBoss = CFrame.new(2288.802, 15.1870775, 863.034607, 0.99974072, -8.41247214e-08, -0.0227668174, 8.4774733e-08, 1, 2.75850098e-08, 0.0227668174, -2.95079072e-08, 0.99974072)
	elseif _G.SelectBoss == "Smoke Admiral [Lv. 1150] [Boss]" then
		MsBoss = "Smoke Admiral [Lv. 1150] [Boss]"
		NameBoss = "Smoke Admiral"
		NameQuestBoss = "IceSideQuest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-6059.96191, 15.9868021, -4904.7373, -0.444992423, -3.0874483e-09, 0.895534337, -3.64098796e-08, 1, -1.4644522e-08, -0.895534337, -3.91229982e-08, -0.444992423)
		CFrameBoss = CFrame.new(-5115.72754, 23.7664986, -5338.2207, 0.251453817, 1.48345061e-08, -0.967869282, 4.02796978e-08, 1, 2.57916977e-08, 0.967869282, -4.54708946e-08, 0.251453817)
	elseif _G.SelectBoss == "Cursed Captain [Lv. 1325] [Raid Boss]" then
		MsBoss = "Cursed Captain [Lv. 1325] [Raid Boss]"
		NameBoss = "Cursed Captain"
		CFrameBoss = CFrame.new(916.928589, 181.092773, 33422, -0.999505103, 9.26310495e-09, 0.0314563364, 8.42916226e-09, 1, -2.6643713e-08, -0.0314563364, -2.63653774e-08, -0.999505103)
	elseif _G.SelectBoss == "Darkbeard [Lv. 1000] [Raid Boss]" then
		MsBoss = "Darkbeard [Lv. 1000] [Raid Boss]"
		NameBoss = "Darkbeard"
		CFrameBoss = CFrame.new(3876.00366, 24.6882591, -3820.21777, -0.976951957, 4.97356325e-08, 0.213458836, 4.57335361e-08, 1, -2.36868622e-08, -0.213458836, -1.33787044e-08, -0.976951957)
	elseif _G.SelectBoss == "Order [Lv. 1250] [Raid Boss]" then
		MsBoss = "Order [Lv. 1250] [Raid Boss]"
		NameBoss = "Order"
		CFrameBoss = CFrame.new(-6221.15039, 16.2351036, -5045.23584, -0.380726993, 7.41463495e-08, 0.924687505, 5.85604774e-08, 1, -5.60738549e-08, -0.924687505, 3.28013137e-08, -0.380726993)
	elseif _G.SelectBoss == "Awakened Ice Admiral [Lv. 1400] [Boss]" then
		MsBoss = "Awakened Ice Admiral [Lv. 1400] [Boss]"
		NameBoss = "Awakened Ice Admiral"
		NameQuestBoss = "FrostQuest"
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(5669.33203, 28.2118053, -6481.55908, 0.921275556, -1.25320829e-08, 0.388910472, 4.72230788e-08, 1, -7.96414241e-08, -0.388910472, 9.17372489e-08, 0.921275556)
		CFrameBoss = CFrame.new(6407.33936, 340.223785, -6892.521, 0.49051559, -5.25310213e-08, -0.871432424, -2.76146022e-08, 1, -7.58250565e-08, 0.871432424, 6.12576301e-08, 0.49051559)
	elseif _G.SelectBoss == "Tide Keeper [Lv. 1475] [Boss]" then
		MsBoss = "Tide Keeper [Lv. 1475] [Boss]"
		 NameBoss = "Tide Keeper"
		NameQuestBoss = "ForgottenQuest"             
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-3053.89648, 236.881363, -10148.2324, -0.985987961, -3.58504737e-09, 0.16681771, -3.07832915e-09, 1, 3.29612559e-09, -0.16681771, 2.73641976e-09, -0.985987961)
		CFrameBoss = CFrame.new(-3570.18652, 123.328949, -11555.9072, 0.465199202, -1.3857326e-08, 0.885206044, 4.0332897e-09, 1, 1.35347511e-08, -0.885206044, -2.72606271e-09, 0.465199202)
	-- Thire World
	elseif _G.SelectBoss == "Stone [Lv. 1550] [Boss]" then
		MsBoss = "Stone [Lv. 1550] [Boss]"
		NameBoss = "Stone"
		NameQuestBoss = "PiratePortQuest"             
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-290, 44, 5577)
		CFrameBoss = CFrame.new(-1085, 40, 6779)
	elseif _G.SelectBoss == "Island Empress [Lv. 1675] [Boss]" then
		MsBoss = "Island Empress [Lv. 1675] [Boss]"
		 NameBoss = "Island Empress"
		NameQuestBoss = "AmazonQuest2"             
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(5443, 602, 752)
		CFrameBoss = CFrame.new(5659, 602, 244)
	elseif _G.SelectBoss == "Kilo Admiral [Lv. 1750] [Boss]" then
		MsBoss = "Kilo Admiral [Lv. 1750] [Boss]"
		NameBoss = "Kilo Admiral"
		NameQuestBoss = "MarineTreeIsland"             
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(2178, 29, -6737)
		CFrameBoss =CFrame.new(2846, 433, -7100)
	elseif _G.SelectBoss == "Captain Elephant [Lv. 1875] [Boss]" then
		MsBoss = "Captain Elephant [Lv. 1875] [Boss]"
		NameBoss = "Captain Elephant"
		NameQuestBoss = "DeepForestIsland"             
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-13232, 333, -7631)
		CFrameBoss = CFrame.new(-13221, 325, -8405)
	elseif _G.SelectBoss == "Beautiful Pirate [Lv. 1950] [Boss]" then
		MsBoss = "Beautiful Pirate [Lv. 1950] [Boss]"
		NameBoss = "Beautiful Pirate"
		NameQuestBoss = "DeepForestIsland2"             
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-12686, 391, -9902)
		CFrameBoss = CFrame.new(5182, 23, -20)
	elseif SelectBoss == "Cake Queen [Lv. 2175] [Boss]" then
		MsBoss = "Cake Queen [Lv. 2175] [Boss]"
		NameQuestBoss = "IceCreamIslandQuest"             
		LevelQuestBoss = 3
		CFrameQuestBoss = CFrame.new(-716, 382, -11010)
		CFrameBoss = CFrame.new(-821, 66, -10965)
	elseif _G.SelectBoss == "rip_indra True Form [Lv. 5000] [Raid Boss]" then
		MsBoss = "rip_indra True Form [Lv. 5000] [Raid Boss]"
		NameBoss = "rip_indra True Form"
		CFrameBoss = CFrame.new(-5359, 424, -2735)
	elseif _G.SelectBoss == "Longma [Lv. 2000] [Boss]" then
		MsBoss = "Longma [Lv. 2000] [Boss]"
		NameBoss = "Longma"
		CFrameBoss = CFrame.new(-10248.3936, 353.79129, -9306.34473)
	elseif _G.SelectBoss == "Soul Reaper [Lv. 2100] [Raid Boss]" then
		MsBoss = "Soul Reaper [Lv. 2100] [Raid Boss]"
		NameBoss = "Soul Reaper"
		CFrameBoss = CFrame.new(-9515.62109, 315.925537, 6691.12012)
	end
end

spawn(function()
	while wait() do
		if _G.AutoBoss then
			pcall(function()
				CheckQuestBoss()
				if game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == false then
					if (CFrameQuestBoss.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 5 then
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", NameQuestBoss, LevelQuestBoss)
						local args = {
							[1] = "SetSpawnPoint"
						}

						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					else
						two(CFrameQuestBoss)
					end
				elseif game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == true then
					if not string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameBoss) then
						local args = {
							[1] = "AbandonQuest"
						}
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					end
					if game:GetService("Workspace").Enemies:FindFirstChild(MsBoss) then
						for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameBoss) then
								if v.Name == MsBoss then
									repeat wait()
										equip(tostring(_G.SelectWeaponB))
										two(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
										v.HumanoidRootPart.CanCollide = false
										v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
										game:GetService("VirtualUser"):CaptureController()
										game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
									until not _G.AutoBoss or v.Humanoid.Health <= 0
								end
							end
						end
					else
						two(CFrameBoss)
					end
				end
			end)
		end
	end
end)


local Stats = win:Tab("Stat")


Stats:Toggle("Melee", _G.Melee,"6022668898", function(Value)
	Melee = Value
end)

Stats:Toggle("Defense", _G.Defense, "6022668898",function(Value)
	Gan = Value
end)

Stats:Toggle("Sword", _G.Sword, "6022668898",function(Value)
	Dap = Value
end)

Stats:Toggle("Gun", _G.Gun,"6022668898", function(Value)
	Pun = Value
end)

Stats:Toggle("Devil Fruit", _G.DevilFruit,"6022668898", function(Value)
	DevilFruit = Value
end)

SelectPoint = 1
Stats:Slider("Point", 1,50,1, function(Point)
	SelectPoint = Point
end)

spawn(function()
	while wait(.1) do
		if Auto_Haki then
			if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
			end
		end
	end
end)

spawn(function()
	while wait(.1) do
		if Melee then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint", "Melee", SelectPoint)
		end
	end
end)

spawn(function()
	while wait(.1) do
		if Gan then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint", "Defense", SelectPoint)
		end
	end
end)

spawn(function()
	while wait(.1) do
		if Dap then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint", "Sword", SelectPoint)
		end
	end
end)

spawn(function()
	while wait(.1) do
		if Pun then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint", "Gun", SelectPoint)
		end
	end
end)

spawn(function()
	while wait(.1) do
		if DevilFruit then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("AddPoint", "Demon Fruit", SelectPoint)
		end
	end
end)


local Game = win:Tab("Game")

Game:Toggle("Auto Superhuman", false,"6022668898",function(vu)
	Superhuman = vu
	if vu then
		local args = {
			[1] = "BuyElectro"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end
end)
Game:Toggle("Auto Superhuman [Full]",false,"6022668898",function(vu)
	SuperhumanFull = vu
end)
-- Auto Death Step
Game:Toggle("Auto Death Step",false,"6022668898",function(vu)
	DeathStep = vu
	if vu then
		local args = {
			[1] = "BuyBlackLeg"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end
end)
-- Auto Dargon Talon
Game:Toggle("Auto Dragon Talon", false,"6022668898",function(vu)
	DargonTalon = vu
	if vu then
		local args = {
			[1] = "BlackbeardReward",
			[2] = "DragonClaw",
			[3] = "2"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end
end)
-- Auto Electric clow
Game:Toggle("Auto Electric Claw", false,"6022668898",function(vu)
	Electricclow = vu
	if vu then
		local args = {
			[1] = "BuyElectro"
		}
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
	end
end)
spawn(function()
	while wait(.25) do
		if Superhuman or SuperhumanFull and game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then 
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Combat") or game.Players.LocalPlayer.Character:FindFirstChild("Combat") then
				local args = {
					[1] = "BuyElectro"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end   
			if game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") or game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") then
				equip("Superhuman")    
			end  
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value <= 299  then
				equip("Black Leg")
			end
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value <= 299  then
				equip("Electro")
			end
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value <= 299  then
				equip("Fishman Karate")
			end
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value <= 299  then
				 equip("Dragon Claw")
			end
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 300  then
				local args = {
					[1] = "BuyFishmanKarate"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end
			if game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 300  then
				local args = {
					[1] = "BuyFishmanKarate"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 100  then
				local args = {
					[1] = "BuyBlackLeg"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end
			if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 300  then
				local args = {
					[1] = "BuyBlackLeg"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 300  then
				if SuperhumanFull and game.Players.LocalPlayer.Data.Fragments.Value < 1500 then
					if game.Players.LocalPlayer.Data.Level.Value > 1100 then
						RaidsSelected = "Flame"
						AutoRaids = true
						RaidsArua = true
					end
				else
					AutoRaids = false
					RaidsArua = false
					local args = {
						[1] = "BlackbeardReward",
						[2] = "DragonClaw",
						[3] = "2"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
			end
			if game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate").Level.Value >= 300  then
				if SuperhumanFull and game.Players.LocalPlayer.Data.Fragments.Value < 1500 then
					if game.Players.LocalPlayer.Data.Level.Value > 1100 then
						RaidsSelected = "Flame"
						AutoRaids = true
						RaidsArua = true
					end
				else
					AutoRaids = false
					RaidsArua = false
					local args = {
						[1] = "BlackbeardReward",
						[2] = "DragonClaw",
						[3] = "2"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
			end
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value >= 300  then
				local args = {
					[1] = "BuySuperhuman"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end
			if game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 300  then
				local args = {
					[1] = "BuySuperhuman"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
			end 
		end
		if DeathStep and game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 400 then
				local args = {
					[1] = "BuyDeathStep"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				equip = "Death Step"
			end  
			if game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 400 then
				local args = {
					[1] = "BuyDeathStep"
				}
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				
				equip = "Death Step"
			end  
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value < 400 then
				equip = "Black Leg"
			end 
		end
		if DargonTalon and game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value <= 399 and game.Players.LocalPlayer.Character.Humanoid.Health > 0 then
				equip = "Dragon Claw"
			end
			if game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value <= 399 and game.Players.LocalPlayer.Character.Humanoid.Health > 0 then
				equip = "Dragon Claw"
			end

			if game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 400 and game.Players.LocalPlayer.Character.Humanoid.Health > 0 then
				equip = "Dragon Claw"
				if game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyDragonTalon", true) == 3 then
					local string_1 = "Bones";
					local string_2 = "Buy";
					local number_1 = 1;
					local number_2 = 1;
					local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
					Target:InvokeServer(string_1, string_2, number_1, number_2);

					local string_1 = "BuyDragonTalon";
					local bool_1 = true;
					local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
					Target:InvokeServer(string_1, bool_1);
				elseif game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyDragonTalon", true) == 1 then
					game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyDragonTalon")
				else
					local string_1 = "BuyDragonTalon";
					local bool_1 = true;
					local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
					Target:InvokeServer(string_1, bool_1);
					local string_1 = "BuyDragonTalon";
					local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
					Target:InvokeServer(string_1);
				end 
			end
		end
		if Electricclow and game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value < 400 then
				
				equip = "Electro"
			end  
			if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value < 400 then
				equip = "Electro"
			end  
			if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 400 then
				local v175 = game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyElectricClaw", true);
				if v175 == 4 then
					local v176 = game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyElectricClaw", "Start");
					if v176 == nil then
						game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-12548, 337, -7481)
					end
				else
					local string_1 = "BuyElectricClaw";
					local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
					Target:InvokeServer(string_1);
				end
			end
			if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 400 then
				local v175 = game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyElectricClaw", true);
				if v175 == 4 then
					local v176 = game.ReplicatedStorage.Remotes.CommF_:InvokeServer("BuyElectricClaw", "Start");
					if v176 == nil then
						game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-12548, 337, -7481)
					end
				else
					local string_1 = "BuyElectricClaw";
					local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
					Target:InvokeServer(string_1);
				end
			end
		end
	end
end)



local Devil = win:Tab("Devil Fruits")
	
SelectDevil = ""
CheckF = false
Devil:Dropdown("AutoBuy DevilFruit",
{
    "Bomb-Bomb",
    "Spike-Spike",
    "Chop-Chop",
    "Spring-Spring",
	"Kilo-Kilo",
	"Spin-Spin",
	"Bird: Falcon",
    "Smoke-Smoke",
    "Flame-Flame",
    "Ice-Ice",
    "Sand-Sand",
    "Dark-Dark",
	"Revive-Revive",
	"Diamond-Diamond",
    "Light-Light",
	"Love-Love",
    "Rubber-Rubber",
    "Barrier-Barrier",
    "Magma-Magma",
	"Door-Door",
    "Quake-Quake",
    "Human-Human: Buddha",
    "String-String",
    "Bird-Bird: Phoenix",
    "Rumble-Rumble",
    "Paw-Paw",
    "Gravity-Gravity",
    "Dough-Dough",
	"Shadow-Shadow",
	"Venom-Venom",
    "Control-Control",
    "Dragon-Dragon",
	"Soul-Soul"
    }
    ,function(ply)
        SelectDevil = ply
end)
Devil:Toggle("Buy Devil Fruit Sinper",false,"6022668898",function(vu)
    BuyFruitSinper = vu
end)
spawn(function()
    while wait(.1) do
        if BuyFruitSinper then
            local args = {
                [1] = "GetFruits"
            }
            
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            local args = {
                [1] = "PurchaseRawFruit",
                [2] = SelectDevil
            }
            
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
        end 
    end
end)

Devil:Toggle("Auto Store Fruit", false,"6022668898", function(vu)
	AutoStoreFruit = vu
end)

spawn(function()
	pcall(function()
		while wait(.1) do
			if AutoStoreFruit then
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Bomb Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Bomb Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Bomb-Bomb")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Spike Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Spike Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Spike-Spike")
                end
                if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Chop Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Chop Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Chop-Chop")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Spring Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Spring Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Spring-Spring")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Kilo Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Kilo Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Kilo-Kilo")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Smoke Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Smoke Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Smoke-Smoke")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Spin Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Spin Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Spin-Spin")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Flame Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flame Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Flame-Flame")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Bird: Falcon Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Bird: Falcon Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Bird-Bird: Falcon")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Ice Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Ice Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Ice-Ice")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Sand Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Sand Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Sand-Sand")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dark Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dark Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Dark-Dark")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Revive Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Revive Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Revive-Dark")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Diamond Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Diamond Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Diamond-Diamond")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Light Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Light Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Light-Light")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Love Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Love Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Love-Love")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Rubber Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Rubber Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Rubber-Rubber")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Barrier Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Barrier Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Barrier-Barrier")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Magma Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Magma Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Magma-Magma")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Door Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Door Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Door-Door")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Quake Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Quake Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Quake-Quake")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Human-Human: Buddha Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Human-Human: Buddha Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Human-Human: Buddha")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("String Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("String Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","String-String")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Bird: Phoenix Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Bird: Phoenix Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Bird-Bird: Phoenix")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Rumble Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Rumble Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Rumble-Rumble")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Paw Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Paw Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Paw-Paw")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Gravity Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Gravity Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Gravity-Gravity")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dough Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dough Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Dough-Dough")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Shadow Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Shadow Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Shadow-Shadow")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Venom Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Venom Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Venom-Venom")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Control Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Control Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Control-Control")
                end
				if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon Fruit") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Dragon Fruit") then
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StoreFruit","Dragon-Dragon")
				end
			end
		end
	end)
end)

Devil:Toggle("Bring Fruit ", _G.BringFruit, "6022668898",function(value)
	BringFruit = value
end)

spawn(function()
	pcall(function()
		while wait(.1) do
            if BringFruit then
                for i,v in pairs(game:GetService("Workspace"):GetChildren()) do
                    if string.find(v.Name, "Fruit") then
                        if v:IsA("Tool") then
                            v.Handle.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, 50, 0)
							wait(.2)
            				firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart,v.Handle,0)
                        end
                    end
                end
            end
        end
	end)
end)



spawn(function()
    while wait() do
        if Drop then
            pcall(function()
                for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
                    if string.find(v.Name, "Fruit") then
                        EquipWeapon(v.Name)
                        SelectFruit = v.Name
                        wait(.1)
                        if game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible == true then
                            game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible = false
                        end
                        EquipWeapon(v.Name)
                        game:GetService("Players").LocalPlayer.Character:FindFirstChild(SelectFruit).EatRemote:InvokeServer("Drop")
                    end
                end
				for i,v in pairs(game:GetService("Players").LocalPlayer.Character:GetChildren()) do
                    if string.find(v.Name, "Fruit") then
                        EquipWeapon(v.Name)
                        SelectFruit = v.Name
                        wait(.1)
                        if game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible == true then
                            game:GetService("Players").LocalPlayer.PlayerGui.Main.Dialogue.Visible = false
                        end
                        EquipWeapon(v.Name)
                        game:GetService("Players").LocalPlayer.Character:FindFirstChild(SelectFruit).EatRemote:InvokeServer("Drop")
                    end
                end
            end)
        end
    end
end)

Devil:Line()



Devil:Toggle("Auto Random Devil Fruit", false, "6022668898",function(v)
    DevilAutoBuy = v
end)

spawn(function()
    while wait(.1) do
        if DevilAutoBuy then
            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Cousin","Buy")
        end
    end
end)





local Players = win:Tab("Players")
function TPISLAND(POS1,POS2)
	local Distance = (POS1 - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
	local Speed = 200 
	tweenService, tweenInfo = game:GetService("TweenService"), TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear)
	tween = tweenService:Create(game:GetService("Players")["LocalPlayer"].Character.HumanoidRootPart, tweenInfo, {CFrame = POS2})
	tween:Play()
	wait(Distance/Speed)
  end 


PlayerName = {}
for i,v in pairs(game.Players:GetChildren()) do  
  table.insert(PlayerName ,v.Name)
end
function isnil(thing)
	return (thing == nil)
end
local function round(n)
	return math.floor(tonumber(n) + 0.5)
end
Number = math.random(1, 1000000)
function UpdatePlayerChams()
	for i,v in pairs(game:GetService'Players':GetChildren()) do
		pcall(function()
			if not isnil(v.Character) then
				if ESPPlayer then
					if not isnil(v.Character.Head) and not v.Character.Head:FindFirstChild('NameEsp'..Number) then
						local bill = Instance.new('BillboardGui',v.Character.Head)
						bill.Name = 'NameEsp'..Number
						bill.ExtentsOffset = Vector3.new(0, 1, 0)
						bill.Size = UDim2.new(1,200,1,30)
						bill.Adornee = v.Character.Head
						bill.AlwaysOnTop = true
						local name = Instance.new('TextLabel',bill)
						name.Font = "GothamBold"
						name.FontSize = "Size14"
						name.TextWrapped = true
						name.Text = (v.Name ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M')
						name.Size = UDim2.new(1,0,1,0)
						name.TextYAlignment = 'Top'
						name.BackgroundTransparency = 1
						name.TextStrokeTransparency = 0.5
						if v.Team == game.Players.LocalPlayer.Team then
							name.TextColor3 = Color3.new(0,255,0)
						else
							name.TextColor3 = Color3.new(255,0,0)
						end
					else
						v.Character.Head['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Character.Head.Position).Magnitude/3) ..' M')
					end
				else
					if v.Character.Head:FindFirstChild('NameEsp'..Number) then
						v.Character.Head:FindFirstChild('NameEsp'..Number):Destroy()
					end
				end
			end
		end)
	end
end
function UpdateChestChams() 
	for i,v in pairs(game.Workspace:GetChildren()) do
		pcall(function()
			if string.find(v.Name,"Chest") then
				if ChestESP then
					if string.find(v.Name,"Chest") then
						if not v:FindFirstChild('NameEsp'..Number) then
							local bill = Instance.new('BillboardGui',v)
							bill.Name = 'NameEsp'..Number
							bill.ExtentsOffset = Vector3.new(0, 1, 0)
							bill.Size = UDim2.new(1,200,1,30)
							bill.Adornee = v
							bill.AlwaysOnTop = true
							local name = Instance.new('TextLabel',bill)
							name.Font = "GothamBold"
							name.FontSize = "Size14"
							name.TextWrapped = true
							name.Size = UDim2.new(1,0,1,0)
							name.TextYAlignment = 'Top'
							name.BackgroundTransparency = 1
							name.TextStrokeTransparency = 0.5
							if v.Name == "Chest1" then
								name.TextColor3 = Color3.fromRGB(109, 109, 109)
								name.Text = ("Chest 1" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
							end
							if v.Name == "Chest2" then
								name.TextColor3 = Color3.fromRGB(173, 158, 21)
								name.Text = ("Chest 2" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
							end
							if v.Name == "Chest3" then
								name.TextColor3 = Color3.fromRGB(85, 255, 255)
								name.Text = ("Chest 3" ..' \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
							end
						else
							v['NameEsp'..Number].TextLabel.Text = (v.Name ..'   \n'.. round((game:GetService('Players').LocalPlayer.Character.Head.Position - v.Position).Magnitude/3) ..' M')
						end
					end
				else
					if v:FindFirstChild('NameEsp'..Number) then
						v:FindFirstChild('NameEsp'..Number):Destroy()
					end
				end
			end
		end)
	end
end



local Player = Players:Dropdown("Selected Player",PlayerName,function(plys)
  _G.SelectP = plys
end)

Players:Button("Refrsh Player",function()
  PlayerName = {}
  Player:Clear()
  for i,v in pairs(game.Players:GetChildren()) do  
	 Player:Add(v.Name)
  end
end)

Players:Button("Teleport to Player",function()
  Distance = (game.Players[_G.SelectP].Character.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
  Speed = 250
  tweenService, tweenInfo = game:GetService("TweenService"), TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear)
  tween = tweenService:Create(game:GetService("Players")["LocalPlayer"].Character.HumanoidRootPart, tweenInfo, {CFrame = game.Players[_G.SelectP].Character.HumanoidRootPart.CFrame})
  tween:Play()
  wait(Distance/Speed)
end)

Players:Toggle("Spectate Player",false,"6022668898",function(bool)
  Sp = bool
  local plr1 = game.Players.LocalPlayer.Character.Humanoid
  local plr2 = game.Players:FindFirstChild(_G.SelectP)
  repeat wait(.1)
	 game.Workspace.Camera.CameraSubject = plr2.Character.Humanoid
  until Sp == false 
  game.Workspace.Camera.CameraSubject = game.Players.LocalPlayer.Character.Humanoid
end)

Players:Toggle("ESP Player",false,"6022668898",function(a)
	ESPPlayer = a
	while ESPPlayer do wait()
		UpdatePlayerChams()
	end
end)



local Tp = win:Tab("Teleport")

function TP2(gotoCFrame)
getgenv().noclip = true
	pcall(function()
		game.Players.LocalPlayer.Character.Humanoid.Sit = false
	end)
	if (game:GetService("Players")["LocalPlayer"].Character:WaitForChild('HumanoidRootPart').Position - gotoCFrame.Position).Magnitude <= 200 then
		pcall(function() 
			tween:Cancel()
		end)
		game:GetService("Players")["LocalPlayer"].Character:WaitForChild('HumanoidRootPart').CFrame = gotoCFrame
	else
		local tween_s = game:service"TweenService"
		local info = TweenInfo.new((game:GetService("Players")["LocalPlayer"].Character:WaitForChild('HumanoidRootPart').Position - gotoCFrame.Position).Magnitude/274, Enum.EasingStyle.Linear)
		local tween, err = pcall(function()
			tween = tween_s:Create(game.Players.LocalPlayer.Character:WaitForChild('HumanoidRootPart'), info, {CFrame = gotoCFrame})
			tween:Play()
			getgenv().noclip = false
		end)
		if not tween then return err end
	end
end



function TP2(P1)
	Distance = (P1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
	if Distance < 1000 then
		Speed = 500
	elseif Distance >= 1000 then
		Speed = 350
	end
	game:GetService("TweenService"):Create(
		game.Players.LocalPlayer.Character.HumanoidRootPart,
		TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
		{CFrame = P1}
	):Play()
	getgenv().noclip = true
	wait(Distance/Speed)
	getgenv().noclip = false
end



function Tween(P1)
	Distance = (P1.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
	if Distance < 1000 then
		Speed = 500
	elseif Distance >= 1000 then
		Speed = 350
	end
	game:GetService("TweenService"):Create(
		game.Players.LocalPlayer.Character.HumanoidRootPart,
		TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
		{CFrame = P1}
	):Play()
	getgenv().noclip = true
	wait(Distance/Speed)
	getgenv().noclip = false
end

function TP(P)
	Distance = (P.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
	if Distance < 10 then
		Speed = 1000
	elseif Distance < 170 then
		game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = P
		Speed = 350
	elseif Distance < 1000 then
		Speed = 350
	elseif Distance >= 1000 then
		Speed = 250
	end
	game:GetService("TweenService"):Create(
		game.Players.LocalPlayer.Character.HumanoidRootPart,
		TweenInfo.new(Distance/Speed, Enum.EasingStyle.Linear),
		{CFrame = P}
	):Play()
end



Tp:Line()
if world1 then

	Tp:Button("First land", function()
		TP2(CFrame.new(1042.1501464844, 16.299360275269, 1444.3442382813))
	end)

	Tp:Button("Marine1", function()
		TP2(CFrame.new(-2599.6655273438, 6.9146227836609, 2062.2216796875))
	end)

	Tp:Button("Marine2", function()
		TP2(CFrame.new(-5081.3452148438, 85.221641540527, 4257.3588867188))
	end)

	Tp:Button("Midle Town", function()
		TP2(CFrame.new(-655.97088623047, 7.878026008606, 1573.7612304688))
	end)

	Tp:Button("Jungle", function()
		TP2(CFrame.new(-1499.9877929688, 22.877912521362, 353.87060546875))
	end)

	Tp:Button("Pirate Village", function()
		TP2(CFrame.new(-1163.3889160156, 44.777843475342, 3842.8276367188))
	end)

	Tp:Button("Desert", function()
		TP2(CFrame.new(954.02056884766, 6.6275520324707, 4262.611328125))
	end)

	Tp:Button("Frozen Village", function()
		TP2(CFrame.new(1144.5270996094, 7.3292083740234, -1164.7322998047))
	end)

	Tp:Button("Colosseum", function()
		TP2(CFrame.new(-1667.5869140625, 39.385631561279, -3135.5817871094))
	end)

	Tp:Button("Prison", function()
		TP2(CFrame.new(4857.6982421875, 5.6780304908752, 732.75750732422))
	end)

	Tp:Button("Mob Leader", function()
		TP2(CFrame.new(-2841.9604492188, 7.3560485839844, 5318.1040039063))
	end)

	Tp:Button("Magma Village", function()
		TP2(CFrame.new(-5328.8740234375, 8.6164798736572, 8427.3994140625))
	end)

	Tp:Button("UnderWater Gate", function()
		TP2(CFrame.new(3893.953125, 5.3989524841309, -1893.4851074219))
	end)


	Tp:Button("Fountain City", function()
		TP2(CFrame.new(5244.7133789063, 38.526943206787, 4073.4987792969))
	end)

	Tp:Button("Sky1", function()
		TP2(CFrame.new(-4878.0415039063, 717.71246337891, -2637.7294921875))
	end)

	Tp:Button("Sky2", function()
		TP2(CFrame.new(-7899.6157226563, 5545.6030273438, -422.21798706055))
	end)

	Tp:Button("Sky3", function()
		TP2(CFrame.new(-7868.5288085938, 5638.205078125, -1482.5548095703))
	end)

	Tp:Line()
	elseif world2 then

	Tp:Button("Dock", function()
		TP2(CFrame.new(-12.519311904907, 19.302536010742, 2827.853515625))
	end)

	Tp:Button("Mansion", function()
		TP2(CFrame.new(-390.34829711914, 321.89730834961, 869.00506591797))
	end)

	Tp:Button("Kingdom Of Rose", function()
		TP2(CFrame.new(-388.29895019531, 138.35575866699, 1132.1662597656))
	end)

	Tp:Button("Cafe", function()
		TP2(CFrame.new(-379.70889282227, 73.0458984375, 304.84692382813))
	end)

	Tp:Button("Sunflower Field", function()
		TP2(CFrame.new(-1576.7171630859, 198.61849975586, 13.725157737732))
	end)

	Tp:Button("Jeramy Mountain", function()
		TP2(CFrame.new(1986.3519287109, 448.95678710938, 796.70239257813))
	end)

	Tp:Button("Colossuem", function()
		TP2(CFrame.new(-1871.8974609375, 45.820514678955, 1359.6843261719))
	end)

	Tp:Button("Factory", function()
		TP2(CFrame.new(349.53750610352, 74.446998596191, -355.62420654297))
	end)

	Tp:Button("The Bridge", function()
		TP2(CFrame.new(-1860.6354980469, 88.384948730469, -1859.1593017578))
	end)

	Tp:Button("Green Bit", function()
		TP2(CFrame.new(-2202.3706054688, 73.097663879395, -2819.2687988281))
	end)

	Tp:Button("Graveyard", function()
		TP2(CFrame.new(-5617.5927734375, 492.22183227539, -778.3017578125))
	end)

	Tp:Button("Dark Area", function()
		TP2(CFrame.new(3464.7700195313, 13.375151634216, -3368.90234375))
	end)

	Tp:Button("Snow Mountain", function()
		TP2(CFrame.new(561.23834228516, 401.44781494141, -5297.14453125))
	end)

	Tp:Button("Hot Island", function()
		TP2(CFrame.new(-5505.9633789063, 15.977565765381, -5366.6123046875))
	end)

	Tp:Button("Cold Island", function()
		TP2(CFrame.new(-5924.716796875, 15.977565765381, -4996.427734375))
	end)

	Tp:Button("Ice Castle", function()
		TP2(CFrame.new(6111.7109375, 294.41259765625, -6716.4829101563))
	end)

	Tp:Button("Usopp's Island", function()
		TP2(CFrame.new(4760.4985351563, 8.3444719314575, 2849.2426757813))
	end)

	Tp:Button("inscription Island", function()
		TP2(CFrame.new(-5099.01171875, 98.241539001465, 2424.4035644531))
	end)

	Tp:Button("Forgotten Island", function()
		TP2(CFrame.new(-3051.9514160156, 238.87203979492, -10250.807617188))
	end)

	Tp:Button("Ghost Ship", function()
		game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
	end) 



	Tp:Line()
	elseif world3 then

	Tp:Button("Port Town", function()
		TP2(CFrame.new(-275.21615600586, 43.755737304688, 5451.0659179688))
	end)

	Tp:Button("Hydra Island", function()
		TP2(CFrame.new(5541.2685546875, 668.30456542969, 195.48069763184))
	end)
	
	Tp:Button("Gaint Tree", function()
		TP2(CFrame.new(2276.0859375, 25.87850189209, -6493.03125))
	end)
	
	Tp:Button("Mansion", function()
		TP2(CFrame.new(-12548.998046875, 332.40396118164, -7603.1865234375))
	end)

	Tp:Button("Castle on the Sea", function()
		TP2(CFrame.new(-5498.0458984375, 313.79473876953, -2860.6022949219))
	end)

	Tp:Button("Graveyard Island", function()
		TP2(CFrame.new(-9515.07324, 142.130615, 5537.58398))
	end)

	Tp:Button("Icecream Island", function()
		TP2(CFrame.new(-880.894531, 118.245354, -11030.7607, -0.867174983, 1.48501234e-09, 0.498003572, 2.70457789e-08, 1, 4.41129586e-08, -0.498003572, 5.1722548e-08, -0.867174983))
	end)

	Tp:Button("Peanut Island", function()
		TP2(CFrame.new(-2124.06738, 44.0723495, -10179.8281, -0.623125494, -2.55908191e-07, -0.782121837, -1.40530574e-07, 1, -2.15235005e-07, 0.782121837, -2.42063933e-08, -0.623125494))
	end)

	Tp:Button("Lab", function()
		TP2(CFrame.new(-5057.146484375, 314.54132080078, -2934.7995605469))
	end)
	end






	local Raid = win:Tab("Auto Raid")


	if world2 then
		Raid:Button("Teleport To Lab", function()
			Tween(CFrame.new(-6438.73535, 250.645355, -4501.50684))
		end)
	elseif world3 then
		Raid:Button("Teleport To DungeonLab", function()
			Tween(CFrame.new(-5057.146484375, 314.54132080078, -2934.7995605469))
		end)
	end
	
	Raid:Dropdown("Select Dungeon", {"Flame","Ice","Quake","Light","Dark","String","Rumble","Magma","Human: Buddha","Sand"}, function(vu)
		_G.SelectRaid = vu
	end)
	
	Raid:Toggle("Kill Aura", false, "6022668898",function(vu)
		Killaura = vu
		
	end)
	
	Raid:Toggle("Auto Awaken", false, "6022668898",function(vu)
		AutoAwakener = vu
	end)
	
	Raid:Toggle("Auto Next Island", false, "6022668898",function(vu)
		NextIsland = vu
	end)
	
	Raid:Line()
	
	Raid:Toggle("Auto Dungeon", false,"6022668898" ,function(vu)
		_G.AutoRaid = vu
		getgenv().noclip = vu
	end)
	
	spawn(function()
		while wait(.1) do
			if _G.AutoRaid or RaidSuperhuman then
				pcall(function()
					if game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Timer.Visible == false then
						if AutoSuperhuman then
							if not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") and not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Special Microchip") or not game:GetService("Players").LocalPlayer.Character:FindFirstChild("Special Microchip") then
								for i,v in pairs(game:GetService("Players").LocalPlayer.Backpack:GetChildren()) do
									if not string.find(v.Name, "Fruit") then
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Cousin","Buy")
									end
								end
							end
						end
						if not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
							game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("RaidsNpc", "Select", _G.SelectRaid)
						end
						if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
							game:GetService("StarterGui"):SetCore("SendNotification",
								{
									Title = "NAO HUB RAID",
									Text = "",
									Icon = "rbxassetid://10258071211",
									Duration = 1
								}
							)
							wait(4)
						end
						if not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") and game.Players.LocalPlayer.Backpack:FindFirstChild("Special Microchip") or  game.Players.LocalPlayer.Character:FindFirstChild("Special Microchip")  then
							if world2 then
								fireclickdetector(game:GetService("Workspace").Map.CircleIsland.RaidSummon2.Button.Main.ClickDetector)
							elseif world3 then
								fireclickdetector(game:GetService("Workspace").Map["Boat Castle"].RaidSummon2.Button.Main.ClickDetector)
							end
						end
					end
				end)
			end
		end
	end)
	
	spawn(function()
		pcall(function()
			while wait(.1) do
				if AutoAwakener then
					local args = {
						[1] = "Awakener",
						[2] = "Check"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
					local args = {
						[1] = "Awakener",
						[2] = "Awaken"
					}
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
				end
			end
		end)
	end)
	
	spawn(function()
		while wait() do
			if Killaura or _G.AutoRaid or RaidSuperhuman then
				for i,v in pairs(game.Workspace.Enemies:GetDescendants()) do
					if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
						pcall(function()
							repeat wait(.1)
								sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
								v.Humanoid.Health = 0
								v.HumanoidRootPart.CanCollide = false
								v.HumanoidRootPart.Size = Vector3.new(50,50,50)
								v.HumanoidRootPart.Transparency = 1
							until not Killaura or not _G.AutoRaid or not RaidSuperhuman or not v.Parent or v.Humanoid.Health <= 0
						end)
					end
				end
			end
		end
	end)
	
	spawn(function()
		pcall(function()
			while game:GetService("RunService").Heartbeat:wait() do
				if NextIsland or RaidSuperhuman or _G.AutoRaid then
					if game:GetService("Players")["LocalPlayer"].PlayerGui.Main.Timer.Visible == true and game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
						if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") then
							TP(game:GetService("Workspace")["_WorldOrigin"].Locations["Island 5"].CFrame*CFrame.new(4,65,10))
						elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") then
							TP(game:GetService("Workspace")["_WorldOrigin"].Locations["Island 4"].CFrame*CFrame.new(4,65,10))
						elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") then
							TP(game:GetService("Workspace")["_WorldOrigin"].Locations["Island 3"].CFrame*CFrame.new(4,65,10))
						elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") then
							TP(game:GetService("Workspace")["_WorldOrigin"].Locations["Island 2"].CFrame*CFrame.new(4,65,10))
						elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
							TP(game:GetService("Workspace")["_WorldOrigin"].Locations["Island 1"].CFrame*CFrame.new(4,65,10))
						end
					elseif New_World then
						TP(CFrame.new(-6438.73535, 250.645355, -4501.50684))
					elseif Three_World then
						TP(CFrame.new(-5057.146484375, 314.54132080078, -2934.7995605469))
					end
				end
			end
		end)
	end)



local BuyItem = win:Tab("BuyItem")

BuyItem:Button("Refund Stat", function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Refund","1")
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Refund","2")
end)

BuyItem:Button("Reroll Race", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Reroll","1")
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Reroll","2")
end)

BuyItem:Line()

BuyItem:Label("Abilities")
BuyItem:Button("Haki", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Buso")
end)
BuyItem:Button("Geppo", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Geppo")
end)
BuyItem:Button("Soru", function()
   game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Soru")
end)
BuyItem:Button("KenHaki", function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk","Buy")
end)

BuyItem:Line()

BuyItem:Label("Fighting Style")

BuyItem:Button("Black Leg", function()
   	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
end)

BuyItem:Button("Electro", function()
   	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
end)

BuyItem:Button("Fishman Karate", function()
   	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
end)

BuyItem:Button("Dragon Claw", function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","1")
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2")
end)

BuyItem:Button("Superhuman", function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
end)
BuyItem:Button("Death Step", function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
end)
BuyItem:Button("Sharkman Karate", function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true)
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
end)
BuyItem:Button("Electric Claw", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw",true)
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
end)

BuyItem:Button("Dragon Talon", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon",true)
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
end)

local Misc = win:Tab("Misc")


Misc:Button("Join Pirates Team", function()
    local args = {
        [1] = "SetTeam",
        [2] = "Pirates"
    }
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args)) 
    local args = {
        [1] = "BartiloQuestProgress"
    }
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
end)

Misc:Button("Join Marines Team",function()
    local args = {
        [1] = "SetTeam",
        [2] = "Marines"
    }
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    local args = {
        [1] = "BartiloQuestProgress"
    }
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
end)

Misc:Line()

Misc:Button("Devil Shop", function()
    local args = {
        [1] = "GetFruits"
    }
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    game.Players.localPlayer.PlayerGui.Main.FruitShop.Visible = true
end)

Misc:Button("Inventory", function()
	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventoryWeapons")
    game.Players.localPlayer.PlayerGui.Main.Inventory.Visible = true
end)

Misc:Button("Awaken", function()
local args = {
    [1] = "getAwakenedAbilities"
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

	game:GetService("Players").LocalPlayer.PlayerGui.Main.AwakeningToggler.Visible = true
end)


Misc:Button("Fruit Inventory", function()

local args = {
    [1] = "getInventoryFruits"
}

game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
game:GetService("Players").LocalPlayer.PlayerGui.Main.FruitInventory.Visible = true
end)


Misc:Button("Color Haki", function()
    game.Players.localPlayer.PlayerGui.Main.Colors.Visible = true
end)

Misc:Button("Title Name", function()
    local args = {
        [1] = "getTitles"
    }
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    game.Players.localPlayer.PlayerGui.Main.Titles.Visible = true
end)


Misc:Line()

Misc:Toggle("No Dodge Cooldown", false, "6022668898",function(Value)
    nododgecool = Value
    NoDodgeCool()
end)


Misc:Toggle("Walk on Water", false,"6022668898", function(vu)
    _G.Water = vu
end)

spawn(function()
    pcall(function()
        while game:GetService("RunService").Heartbeat:wait() do
            if _G.Water then
                if game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame.Y <= 1 then
                    if not game:GetService("Workspace"):FindFirstChild("Water") then
                        local Water = Instance.new("Part", game.Workspace)
                        Water.Name = "Water"
                        Water.Size = Vector3.new(10,0.5,10)
                        Water.Transparency = 1
                        Water.Anchored = true
                        game:GetService("Workspace").Water.CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.X,game:GetService("Workspace").Camera["Water;"].CFrame.Y,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Z)
                    else
                        game:GetService("Workspace").Water.CFrame = CFrame.new(game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.X,game:GetService("Workspace").Camera["Water;"].CFrame.Y,game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Z)
                    end
                elseif game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame.Y >= 1 and game:GetService("Workspace"):FindFirstChild("Water") then
                    game:GetService("Workspace"):FindFirstChild("Water"):Destroy()
                end
            else
                if game:GetService("Workspace"):FindFirstChild("Water") then
                    game:GetService("Workspace"):FindFirstChild("Water"):Destroy()
                end
            end
        end
    end)
end)








nododgecool = false
function NoDodgeCool()
    if nododgecool then
        for i,v in next, getgc() do
            if game.Players.LocalPlayer.Character.Dodge then
                if typeof(v) == "function" and getfenv(v).script == game.Players.LocalPlayer.Character.Dodge then
                    for i2,v2 in next, getupvalues(v) do
                        if tostring(v2) == "0.4" then
                            repeat wait(.1)
                                setupvalue(v,i2,0)
                            until not nododgecool
                        end
                    end
                end
            end
        end
    end
end

Misc:Line()








Misc:Button("Rejoin Server", function()
	game:GetService("TeleportService"):Teleport(game.PlaceId, game:GetService("Players").localPlayer)
end)
local function HttpGet(url)
	return game:GetService("HttpService"):JSONDecode(htgetf(url))
end

Misc:Button("Server Hop",function()
	local StarterGui = game:GetService("StarterGui")
StarterGui:SetCore("SendNotification", {
    Title = "NaoHub";
    Text = "Wait For Hop Server";
    Icon = "rbxassetid://10258071211";
})
wait(1)
pcall(function()
    for count = math.random(1, math.random(40, 75)), 100 do
        local args = {
        [1] = count
    }
    remote = game:GetService("ReplicatedStorage").__ServerBrowser:InvokeServer(unpack(args))
    for _i ,v in pairs(remote) do
        for _i2 ,v2 in pairs(v) do
            if tonumber(v['Count']) < 12 then
                if string.find(v['Region'], 'Sing') then
                    game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, _i)
                end
            end
        end    
    end    
    end
end)
end)

Misc:Button("Hop Low People", function()
	local StarterGui = game:GetService("StarterGui")
	StarterGui:SetCore("SendNotification", {
		Title = "NaoHub";
		Text = "กดหลายๆครั้งเลย";
		Icon = "rbxassetid://10258071211";
	})
	pcall(function()
    for count = math.random(1, math.random(40, 75)), 100 do
        local args = {
        [1] = count
    }
    remote = game:GetService("ReplicatedStorage").__ServerBrowser:InvokeServer(unpack(args))
    for _i ,v in pairs(remote) do
        for _i2 ,v2 in pairs(v) do
            if tonumber(v['Count']) < 5 then
                if string.find(v['Region'], 'Sing') then
                    game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, _i)
                end
            end
        end    
    end    
    end
end)
end)


local ScreenGui = Instance.new("ScreenGui")
local TextLabel = Instance.new("TextLabel")
local UIGradient = Instance.new("UIGradient")

ScreenGui.Parent = game.CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

TextLabel.Parent = ScreenGui
TextLabel.Active = true
TextLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.BackgroundTransparency = 1.000
TextLabel.BorderColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.Position = UDim2.new(0.474810000, 0, 0, 0)
TextLabel.Size = UDim2.new(0, 200, 0, 50)
TextLabel.Font = Enum.Font.GothamBold
TextLabel.Text = "Server Time"
TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.TextSize = 25.000
TextLabel.TextTransparency = 1
TextLabel.TextStrokeTransparency = 300.000

UIGradient.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(0, 128, 255)), ColorSequenceKeypoint.new(0.50, Color3.fromRGB(0, 128, 255)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(0, 128, 255))}
UIGradient.Parent = TextLabel

local function UpdateTime()
	local GameTime = math.floor(workspace.DistributedGameTime+0.5)
	local Hour = math.floor(GameTime/(60^2))%24
	local Minute = math.floor(GameTime/(60^1))%60
	local Second = math.floor(GameTime/(60^0))%60
	TextLabel.Text = ("Hour : "..Hour.." Minute : "..Minute.." Second : "..Second)
end



function HopLowerServer()
	local maxplayers, gamelink, goodserver, data_table = math.huge, "https://games.roblox.com/v1/games/" .. game.PlaceId .. "/servers/Public?sortOrder=Asc&limit=100"
	if not _G.FailedServerID then _G.FailedServerID = {} end
	local function serversearch()
		data_table = game:GetService"HttpService":JSONDecode(game:HttpGetAsync(gamelink))
		for _, v in pairs(data_table.data) do
			pcall(function()
				if type(v) == "table" and v.id and v.playing and tonumber(maxplayers) > tonumber(v.playing) and not table.find(_G.FailedServerID, v.id) then
					maxplayers = v.playing
					goodserver = v.id
				end
			end)
		end
	end
	function getservers()
		pcall(serversearch)
		for i, v in pairs(data_table) do
			if i == "nextPageCursor" then
				if gamelink:find"&cursor=" then
					local a = gamelink:find"&cursor="
					local b = gamelink:sub(a)
					gamelink = gamelink:gsub(b, "")
				end
				gamelink = gamelink .. "&cursor=" .. v
				pcall(getservers)
			end
		end
	end
	pcall(getservers)
	if goodserver == game.JobId or maxplayers == #game:GetService"Players":GetChildren() - 1 then
	end
	table.insert(_G.FailedServerID, goodserver)
	game:GetService"TeleportService":TeleportToPlaceInstance(game.PlaceId, goodserver)
end




spawn(function()
	while true do
		UpdateTime()
		game:GetService("RunService").RenderStepped:Wait()
	end
end)





Misc:Line()

Misc:Toggle("Server Time",false,"6022668898",function(value)
	ServerTime = value
	if ServerTime == true then
		TextLabel.TextTransparency = 0
	elseif ServerTime == false then
		TextLabel.TextTransparency = 1
	end
end)


Misc:Button("FPS Boost", function()
	FPSBOOT()
end)

function FPSBOOT()
    pcall(function()
        game:GetService("Lighting").FantasySky:Destroy()
        local decalsyeeted = true -- Leaving this on makes games look shitty but the fps goes up by at least 20.
        local g = game
        local w = g.Workspace
        local l = g.Lighting
        local t = w.Terrain
        t.WaterWaveSize = 0
        t.WaterWaveSpeed = 0
        t.WaterReflectance = 0
        t.WaterTransparency = 0
        l.GlobalShadows = false
        l.FogEnd = 9e9
        l.Brightness = 0
        settings().Rendering.QualityLevel = "Level01"
        for i, v in pairs(g:GetDescendants()) do
            if v:IsA("Part") or v:IsA("Union") or v:IsA("CornerWedgePart") or v:IsA("TrussPart") then 
                    v.Material = "Plastic"
                    v.Reflectance = 0
                    --v.CanCollide = false
            elseif v:IsA("Decal") or v:IsA("Texture") and decalsyeeted then
                    v.Transparency = 1
            elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
                    v.Lifetime = NumberRange.new(0)
            elseif v:IsA("Explosion") then
                    v.BlastPressure = 1
                    v.BlastRadius = 1
            elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
                    v.Enabled = false
            elseif v:IsA("MeshPart") then
                    v.Material = "Plastic"
                    v.Reflectance = 0
                    v.TextureID = 10385902758728957
                    
            end
        end
        for i, e in pairs(l:GetChildren()) do
            if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then
                    e.Enabled = false
            end
        end
        for i, v in pairs(game:GetService("Workspace").Camera:GetDescendants()) do
            if v.Name == ("Water;") then
                v.Transparency = 1
                v.Material = "Plastic"
            end
        end
    end)
end


Misc:Toggle("White Screen",false,"6022668898",function(value)
	_G.Ws = value
end)

spawn(function()
	while task.wait() do
		if _G.Ws == true then
			game:GetService("RunService"):Set3dRenderingEnabled(false)
		elseif _G.Ws == false then
			game:GetService("RunService"):Set3dRenderingEnabled(true)
		end
	end
end)




-----------------------------------------------------------UI

local placeId = game.PlaceId
if placeId == 2753915549 then
    world1 = true
elseif placeId == 4442272183 then
    world2 = true
elseif placeId == 7449423635 then
    world3 = true
end


function two(gotoCFrame)
	pcall(function()
		game.Players.LocalPlayer.Character.Humanoid.Sit = false
	end)
	if (game:GetService("Players")["LocalPlayer"].Character:WaitForChild('HumanoidRootPart').Position - gotoCFrame.Position).Magnitude <= 200 then
		pcall(function() 
			tween:Cancel()
		end)
		game:GetService("Players")["LocalPlayer"].Character:WaitForChild('HumanoidRootPart').CFrame = gotoCFrame
	else
		local tween_s = game:service"TweenService"
		local info = TweenInfo.new((game:GetService("Players")["LocalPlayer"].Character:WaitForChild('HumanoidRootPart').Position - gotoCFrame.Position).Magnitude/300, Enum.EasingStyle.Linear)
		local tween, err = pcall(function()
			tween = tween_s:Create(game.Players.LocalPlayer.Character:WaitForChild('HumanoidRootPart'), info, {CFrame = gotoCFrame})
			tween:Play()
		end)
		if not tween then return err end
	end
end










-------------------------------------------------------------



function checklevel()
   local MYLEVEL = game:GetService("Players").LocalPlayer.Data.Level.Value
   if world1 then
		magbring = 240
		if MYLEVEL == 1 or MYLEVEL <= 9 then
		magbring = 400
		Ms = "Bandit [Lv. 5]"
		NameQuest = "BanditQuest1"
		QuestLv = 1
		NameQ = "Bandit"
		CFrameQ = CFrame.new(1060.61548, 16.5166187, 1546.06348, -0.966731012, 9.64880797e-08, 0.255795151, 8.52720916e-08, 1, -5.49381056e-08, -0.255795151, -3.12981818e-08, -0.966731012)
		CFramePuk = CFrame.new(1094.74158, 68.1195679, 1617.98132, -0.805238843, 2.58748241e-06, -0.592950821, 6.83637325e-07, 1, 3.43534839e-06, 0.592950821, 2.36091159e-06, -0.805238843)
		elseif MYLEVEL == 10 or MYLEVEL <= 14 then
		magbring = 400
		Ms = "Monkey [Lv. 14]"
		NameQuest = "JungleQuest"
		QuestLv = 1
		NameQ = "Monkey"
		CFrameQ = CFrame.new(-1600.24353, 36.8521347, 153.224792, 0.0664860159, 1.09421023e-07, -0.997787356, 9.55680779e-09, 1, 1.10300476e-07, 0.997787356, -1.68691017e-08, 0.0664860159)
		CFramePuk = CFrame.new(-1609.71216, 39.8521576, 123.384674, 0.708323717, 6.74341152e-08, 0.705887735, -1.86098941e-08, 1, -7.68568071e-08, -0.705887735, 4.13030072e-08, 0.708323717)
		elseif MYLEVEL == 15 or MYLEVEL <= 29 then
		magbring = 240
		Ms = "Gorilla [Lv. 20]"
		NameQuest = "JungleQuest"
		QuestLv = 2
		NameQ = "Gorilla"
		CFrameQ = CFrame.new(-1600.24353, 36.8521347, 153.224792, 0.0664860159, 1.09421023e-07, -0.997787356, 9.55680779e-09, 1, 1.10300476e-07, 0.997787356, -1.68691017e-08, 0.0664860159)
		CFramePuk = CFrame.new(-1260.29321, 18.6214619, -398.3508, 0.816335142, 5.76316722e-07, -0.577578545, 8.32609999e-08, 1, 1.11549434e-06, 0.577578545, -9.58707005e-07, 0.816335142)
		elseif MYLEVEL == 30 or MYLEVEL <= 39 then
		Ms = "Pirate [Lv. 35]"
		NameQuest = "BuggyQuest1"
		QuestLv = 1
		NameQ = "Pirate"
		CFrameQ = CFrame.new(-1139.56116, 4.75204945, 3825.97827, -0.947666645, 2.60038924e-08, 0.319261551, 3.65571005e-08, 1, 2.70626153e-08, -0.319261551, 3.73176157e-08, -0.947666645)
		CFramePuk = CFrame.new(-1223.64111, 4.75204945, 3914.84668, -0.99005419, 5.39223821e-09, 0.140686572, -6.35229591e-10, 1, -4.27983267e-08, -0.140686572, -4.24620303e-08, -0.99005419)
		elseif MYLEVEL == 40 or MYLEVEL <= 59 then
		Ms = "Brute [Lv. 45]"
		NameQuest = "BuggyQuest1"
		QuestLv = 2
		NameQ = "Brute"
		CFrameQ = CFrame.new(-1139.56116, 4.75204945, 3825.97827, -0.947666645, 2.60038924e-08, 0.319261551, 3.65571005e-08, 1, 2.70626153e-08, -0.319261551, 3.73176157e-08, -0.947666645)
		CFramePuk = CFrame.new(-1140.92944, 14.8098745, 4317.16455, -0.943479657, 3.71900555e-08, -0.331430465, 1.7316566e-08, 1, 6.2915845e-08, 0.331430465, 5.36205853e-08, -0.943479657)
		elseif MYLEVEL == 60 or MYLEVEL <= 74 then
		Ms = "Desert Bandit [Lv. 60]"
		NameQuest = "DesertQuest"
		QuestLv = 1
		NameQ = "Desert Bandit"
		CFrameQ = CFrame.new(896.408142, 6.43846178, 4389.37891, -0.846945703, -2.31297754e-08, 0.531679392, -1.55507234e-08, 1, 1.87315088e-08, -0.531679392, 7.59657048e-09, -0.846945703)
		CFramePuk = CFrame.new(949.532593, 15.2893953, 4403.09912, -0.832314849, -4.19622452e-08, 0.55430311, 7.94023236e-10, 1, 7.68949704e-08, -0.55430311, 6.44409539e-08, -0.832314849)
		elseif MYLEVEL == 75 or MYLEVEL <= 89 then
		Ms = "Desert Officer [Lv. 70]"
		NameQuest = "DesertQuest"
		QuestLv = 2
		NameQ = "Desert Officer"
		CFrameQ = CFrame.new(896.408142, 6.43846178, 4389.37891, -0.846945703, -2.31297754e-08, 0.531679392, -1.55507234e-08, 1, 1.87315088e-08, -0.531679392, 7.59657048e-09, -0.846945703)
		CFramePuk = CFrame.new(1547.40369, 14.4520388, 4359.40625, 0.228631318, -1.20783e-07, -0.973513126, -3.43095508e-08, 1, -1.32126871e-07, 0.973513126, 6.36091286e-08, 0.228631318)
		elseif MYLEVEL == 90 or MYLEVEL <= 99 then
		Ms = "Snow Bandit [Lv. 90]"
		NameQuest = "SnowQuest"
		QuestLv = 1
		NameQ = "Snow Bandit"
		CFrameQ = CFrame.new(1384.01538, 87.272789, -1296.28137, 0.462413222, -7.79864777e-08, -0.88666451, -1.42050363e-08, 1, -9.53630916e-08, 0.88666451, 5.6692258e-08, 0.462413222)
		CFramePuk = CFrame.new(1372.84326, 105.990303, -1422.19507, 0.719091773, -2.12436309e-08, 0.694915235, 9.82151036e-08, 1, -7.10619616e-08, -0.694915235, 1.19351228e-07, 0.719091773)
		elseif MYLEVEL == 100 or MYLEVEL <= 119 then
		Ms = "Snowman [Lv. 100]"
		NameQuest = "SnowQuest"
		QuestLv = 2
		NameQ = "Snowman"
		CFrameQ = CFrame.new(1384.01538, 87.272789, -1296.28137, 0.462413222, -7.79864777e-08, -0.88666451, -1.42050363e-08, 1, -9.53630916e-08, 0.88666451, 5.6692258e-08, 0.462413222)
		CFramePuk = CFrame.new(1220.92712, 138.011871, -1489.01208, 0.389352709, -7.53626693e-07, 0.921088696, 1.45705499e-07, 1, 7.56600116e-07, -0.921088696, -1.60376572e-07, 0.389352709)
		elseif MYLEVEL == 120 or MYLEVEL <= 149 then
		Ms = "Chief Petty Officer [Lv. 120]"
		NameQuest = "MarineQuest2"
		QuestLv = 1
		NameQ = "Chief Petty Officer"
		CFrameQ = CFrame.new(-5034.64893, 28.6520348, 4324.53369, -0.0616381466, 5.83357576e-08, 0.998098552, -1.59750098e-08, 1, -5.9433436e-08, -0.998098552, -1.96080023e-08, -0.0616381466)
		CFramePuk = CFrame.new(-4863.61328, 22.6520348, 4306.39307, 0.536051273, 7.00434066e-09, -0.844185412, -5.8011751e-10, 1, 7.92878918e-09, 0.844185412, -3.76051057e-09, 0.536051273)
		elseif MYLEVEL == 150 or MYLEVEL <= 174 then
		Ms = "Sky Bandit [Lv. 150]"
		NameQuest = "SkyQuest"
		QuestLv = 1
		NameQ = "Sky Bandit"
		CFrameQ = CFrame.new(-4843.2041, 717.669617, -2623.13159, -0.775086224, -1.6359829e-08, -0.631855488, -4.10942462e-08, 1, 2.45178793e-08, 0.631855488, 4.49690951e-08, -0.775086224)
		CFramePuk = CFrame.new(-4970.74219, 294.544342, -2890.11353, -0.994874597, -8.61311165e-08, -0.101116329, -9.10836278e-08, 1, 4.43614923e-08, 0.101116329, 5.33441664e-08, -0.994874597)
		elseif MYLEVEL == 175 or MYLEVEL <= 189 then
		Ms = "Dark Master [Lv. 175]"
		NameQuest = "SkyQuest"
		QuestLv = 2
		NameQ = "Dark Master"
		CFrameQ = CFrame.new(-4843.2041, 717.669617, -2623.13159, -0.775086224, -1.6359829e-08, -0.631855488, -4.10942462e-08, 1, 2.45178793e-08, 0.631855488, 4.49690951e-08, -0.775086224)
		CFramePuk = CFrame.new(-5239.94629, 392.217102, -2208.18335, 0.969297886, -5.95604988e-09, -0.245889395, 3.87897714e-09, 1, -8.93151775e-09, 0.245889395, 7.70350184e-09, 0.969297886)
		elseif MYLEVEL == 190 or MYLEVEL <= 209 then
		Ms = "Prisoner [Lv. 190]"
		NameQuest = "PrisonerQuest"
		QuestLv = 1
		NameQ = "Prisoner"
		CFrameQ = CFrame.new(5307.95166015625, 1.6809712648391724, 475.1698913574219)
		CFramePuk = CFrame.new(5029.708984375, 68.67806243896484, 445.857177734375)
		elseif MYLEVEL == 210 or MYLEVEL <= 249 then
		Ms = "Dangerous Prisoner [Lv. 210]"
		NameQuest = "PrisonerQuest"
		QuestLv = 2
		NameQ = "Dangerous Prisoner"
		CFrameQ = CFrame.new(5307.95166015625, 1.6809712648391724, 475.1698913574219)
		CFramePuk = CFrame.new(5673.51758, 68.6786652, 783.757629, -0.0514698699, 7.78369369e-08, 0.998674572, 8.35602094e-08, 1, -7.36337e-08, -0.998674572, 7.96595359e-08, -0.0514698699)
		elseif MYLEVEL == 250 or MYLEVEL <= 274 then
		Ms = "Toga Warrior [Lv. 250]"
		NameQuest = "ColosseumQuest"
		QuestLv = 1
		NameQ = "Toga Warrior"
		CFrameQ = CFrame.new(-1575.72961, 7.38933659, -2983.39453, 0.52762109, -1.48187587e-06, 0.849479854, 2.69328297e-07, 1, 1.57716818e-06, -0.849479854, -6.0335816e-07, 0.52762109)
		CFramePuk = CFrame.new(-1819.12415, 7.28907108, -2744.02539, 0.547199547, 2.10840998e-08, -0.837002158, -1.27399286e-10, 1, 2.51067309e-08, 0.837002158, -1.36317579e-08, 0.547199547)
		elseif MYLEVEL == 275 or MYLEVEL <= 299 then
		Ms = "Gladiator [Lv. 275]"
		NameQuest = "ColosseumQuest"
		QuestLv = 2
		NameQ = "Gladiator"
		CFrameQ = CFrame.new(-1575.72961, 7.38933659, -2983.39453, 0.52762109, -1.48187587e-06, 0.849479854, 2.69328297e-07, 1, 1.57716818e-06, -0.849479854, -6.0335816e-07, 0.52762109)
		CFramePuk = CFrame.new(-1334.76514, 7.44254398, -3228.90552, -0.340173125, 2.8230156e-08, 0.940362811, 2.60959143e-09, 1, -2.90764834e-08, -0.940362811, -7.4370754e-09, -0.340173125)
		elseif MYLEVEL == 300 or MYLEVEL <= 324 then
		Ms = "Military Soldier [Lv. 300]"
		NameQuest = "MagmaQuest"
		QuestLv = 1
		NameQ = "Military Soldier"
		CFrameQ = CFrame.new(-5316.33887, 12.236989, 8517.67285, 0.499506682, -5.08374072e-08, -0.86631006, -1.30872131e-08, 1, -6.62286652e-08, 0.86631006, 4.44192452e-08, 0.499506682)
		CFramePuk = CFrame.new(-5419.0752, 10.9255161, 8464.50488, -0.637788415, -4.55103836e-05, 0.770211577, 7.05542743e-06, 1, 6.49305366e-05, -0.770211577, 4.68461185e-05, -0.637788415)
		elseif MYLEVEL == 325 or MYLEVEL <= 374 then
		Ms = "Military Spy [Lv. 325]"
		NameQuest = "MagmaQuest"
		QuestLv = 2
		NameQ = "Military Spy"
		CFrameQ = CFrame.new(-5316.33887, 12.236989, 8517.67285, 0.499506682, -5.08374072e-08, -0.86631006, -1.30872131e-08, 1, -6.62286652e-08, 0.86631006, 4.44192452e-08, 0.499506682)
		CFramePuk = CFrame.new(-5805.42041, 99.5276108, 8782.36719, -0.316935152, -6.4923519e-08, 0.948447227, 4.12987404e-08, 1, 8.2252896e-08, -0.948447227, 6.52385026e-08, -0.316935152)
		elseif MYLEVEL == 375 or MYLEVEL <= 399 then
		Ms = "Fishman Warrior [Lv. 375]"
		NameQuest = "FishmanQuest"
		QuestLv = 1
		NameQ = "Fishman Warrior"
		CFrameQ = CFrame.new(61122.2422, 18.4716377, 1568.84778, 0.971045971, -1.77007031e-08, 0.238892734, 4.80190776e-09, 1, 5.45760841e-08, -0.238892734, -5.18487475e-08, 0.971045971)
		CFramePuk = CFrame.new(60898.043, 18.4828224, 1550.9906, -0.0750192106, -4.46996573e-09, 0.997182071, 3.6461556e-10, 1, 4.51002746e-09, -0.997182071, 7.0192685e-10, -0.0750192106)
		if _G.Autofram and (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 3000 then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
		end
		elseif MYLEVEL == 400 or MYLEVEL <= 449 then
		Ms = "Fishman Commando [Lv. 400]"
		NameQuest = "FishmanQuest"
		QuestLv = 2
		NameQ = "Fishman Commando"
		CFrameQ = CFrame.new(61122.2422, 18.4716377, 1568.84778, 0.971045971, -1.77007031e-08, 0.238892734, 4.80190776e-09, 1, 5.45760841e-08, -0.238892734, -5.18487475e-08, 0.971045971)
		CFramePuk = CFrame.new(61885.4063, 18.4828224, 1500.37195, 0.722261012, 4.84021889e-08, -0.691620588, 1.27929427e-08, 1, 8.33434299e-08, 0.691620588, -6.90435726e-08, 0.722261012)
		if _G.Autofram and (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 3000 then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
		end
		elseif MYLEVEL == 450 or MYLEVEL <= 474 then
		Ms = "God's Guard [Lv. 450]"
		NameQuest = "SkyExp1Quest"
		QuestLv = 1
		NameQ = "God's Guard"
		CFrameQ = CFrame.new(-4721.28369, 845.277161, -1954.95154, -0.979754269, -1.72096932e-08, 0.200205252, -2.52417198e-09, 1, 7.36076018e-08, -0.200205252, 7.16119786e-08, -0.979754269)
		CFramePuk = CFrame.new(-4630.00635, 866.902954, -1936.76331, -0.656243384, 9.12737941e-12, 0.754549265, 3.58402819e-09, 1, 3.10498938e-09, -0.754549265, 4.74195483e-09, -0.656243384)
		if _G.Autofram and (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 3000 then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
		end
		elseif MYLEVEL == 475 or MYLEVEL <= 524 then
		Ms = "Shanda [Lv. 475]"
		NameQuest = "SkyExp1Quest"
		QuestLv = 2
		NameQ = "Shanda"
		CFrameQ = CFrame.new(-7861.79736, 5545.49316, -379.920776, 0.504107952, -1.41941534e-08, -0.863640666, -1.31181936e-08, 1, -2.40923566e-08, 0.863640666, 2.34745521e-08, 0.504107952)
		CFramePuk = CFrame.new(-7682.69775, 5607.36279, -445.691833, 0.786274791, -4.48163426e-08, -0.617877364, -4.81674345e-09, 1, -7.86622607e-08, 0.617877364, 6.48263239e-08, 0.786274791)
		if _G.Autofram and (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 3000 then
			game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
		end
		elseif MYLEVEL == 525 or MYLEVEL <= 549 then
		Ms = "Royal Squad [Lv. 525]"
		NameQuest = "SkyExp2Quest"
		QuestLv = 1
		NameQ = "Royal Squad"
		CFrameQ = CFrame.new(-7902.23242, 5635.96387, -1411.96741, -0.0435957126, -2.13718043e-09, 0.999049246, 4.23562352e-10, 1, 2.15769735e-09, -0.999049246, 5.1722604e-10, -0.0435957126)
		CFramePuk = CFrame.new(-7579.42285, 5628.39111, -1540.75073, -0.0374937952, 1.17099557e-08, 0.999296963, -3.30279164e-08, 1, -1.29574085e-08, -0.999296963, -3.34905081e-08, -0.0374937952)
		elseif MYLEVEL == 550 or MYLEVEL <= 624 then
		Ms = "Royal Soldier [Lv. 550]"
		NameQuest = "SkyExp2Quest"
		QuestLv = 2
		NameQ = "Royal Soldier"
		CFrameQ = CFrame.new(-7902.23242, 5635.96387, -1411.96741, -0.0435957126, -2.13718043e-09, 0.999049246, 4.23562352e-10, 1, 2.15769735e-09, -0.999049246, 5.1722604e-10, -0.0435957126)
		CFramePuk = CFrame.new(-7834.84717, 5681.36182, -1790.76782, -0.102890432, 3.28112684e-08, 0.994692683, -6.45397762e-08, 1, -3.96622966e-08, -0.994692683, -6.82781121e-08, -0.102890432)
		elseif MYLEVEL == 625 or MYLEVEL <= 649 then
		Ms = "Galley Pirate [Lv. 625]"
		NameQuest = "FountainQuest"
		QuestLv = 1
		NameQ = "Galley Pirate"
		CFrameQ = CFrame.new(5254.52734, 38.5011368, 4049.80127, -0.0732342899, 2.23174847e-08, -0.997314751, 1.2052287e-07, 1, 1.35274023e-08, 0.997314751, -1.19208565e-07, -0.0732342899)
		CFramePuk = CFrame.new(5597.58936, 41.5013657, 3960.55371, -0.584786832, 4.98908861e-08, 0.811187029, 4.10757259e-08, 1, -3.18919575e-08, -0.811187029, 1.4670098e-08, -0.584786832)
		elseif MYLEVEL >= 650 then
		Ms = "Galley Captain [Lv. 650]"
		NameQuest = "FountainQuest"
		QuestLv = 2
		NameQ = "Galley Captain"
		CFrameQ = CFrame.new(5254.52734, 38.5011368, 4049.80127, -0.0732342899, 2.23174847e-08, -0.997314751, 1.2052287e-07, 1, 1.35274023e-08, 0.997314751, -1.19208565e-07, -0.0732342899)
		CFramePuk = CFrame.new(5705.8252, 52.241478, 4890.11035, -0.969319642, 4.40228476e-09, 0.245803744, -7.88622412e-09, 1, -4.90088397e-08, -0.245803744, -4.94436954e-08, -0.969319642)    
		end
		end
		if world2 then
			magbring = 400
			if MYLEVEL == 700 or MYLEVEL <= 724 then
			Ms = "Raider [Lv. 700]"
			NameQuest = "Area1Quest"
			QuestLv = 1
			NameQ = "Raider"
			CFrameQ = CFrame.new(-424.080078, 73.0055847, 1836.91589, 0.253544956, -1.42165932e-08, 0.967323601, -6.00147771e-08, 1, 3.04272909e-08, -0.967323601, -6.5768397e-08, 0.253544956)
			CFramePuk = CFrame.new(-141.872437, 96.6845093, 2491.01538, 0.13152431, 0, -0.991312981, -0, 1.00000012, -0, 0.991312981, 0, 0.13152431)
			elseif MYLEVEL == 725 or MYLEVEL <= 774 then
			Ms = "Mercenary [Lv. 725]"
			NameQuest = "Area1Quest"
			QuestLv = 2
			NameQ = "Mercenary"
			CFrameQ = CFrame.new(-424.080078, 73.0055847, 1836.91589, 0.253544956, -1.42165932e-08, 0.967323601, -6.00147771e-08, 1, 3.04272909e-08, -0.967323601, -6.5768397e-08, 0.253544956)
			CFramePuk = CFrame.new(-938.497314, 80.9546738, 1443.98608, 0.231955677, 0, 0.972726345, -0, 1, -0, -0.972726345, 0, 0.231955677)
			elseif MYLEVEL == 775 or MYLEVEL <= 874 then
			Ms = "Swan Pirate [Lv. 775]"
			NameQuest = "Area2Quest"
			QuestLv = 1
			NameQ = "Swan Pirate"
			CFrameQ = CFrame.new(632.698608, 73.1055908, 918.666321, -0.0319722369, 8.96074881e-10, -0.999488771, 1.36326533e-10, 1, 8.92172336e-10, 0.999488771, -1.07732087e-10, -0.0319722369)
			CFramePuk = CFrame.new(967.233276, 141.309494, 1210.06384, 0.999673784, 5.40161649e-09, -0.0255404469, -7.62258967e-09, 1, -8.68617107e-08, 0.0255404469, 8.7028063e-08, 0.999673784)
			elseif MYLEVEL == 875 or MYLEVEL <= 899 then
			Ms = "Marine Lieutenant [Lv. 875]"
			NameQuest = "MarineQuest3"
			QuestLv = 1
			NameQ = "Marine Lieutenant."
			CFrameQ = CFrame.new(-2443.04639, 73.0161057, -3220.30225, -0.854058921, -6.13997599e-08, -0.520176232, -1.30658604e-08, 1, -9.65840883e-08, 0.520176232, -7.56919505e-08, -0.854058921)
			CFramePuk = CFrame.new(-2967.00757, 72.9661407, -2972.7478, 0.977851391, 8.27619218e-08, -0.209300488, -6.95268412e-08, 1, 7.05923142e-08, 0.209300488, -5.44767893e-08, 0.977851391)
			elseif MYLEVEL == 900 or MYLEVEL <= 949 then
			Ms = "Marine Captain [Lv. 900]"
			NameQuest = "MarineQuest3"
			QuestLv = 2
			NameQ = "Marine Captain"
			CFrameQ = CFrame.new(-2443.04639, 73.0161057, -3220.30225, -0.854058921, -6.13997599e-08, -0.520176232, -1.30658604e-08, 1, -9.65840883e-08, 0.520176232, -7.56919505e-08, -0.854058921)
			CFramePuk = CFrame.new(-1818.36401, 93.3760834, -3203.57788, 0.315930545, 4.84752114e-08, 0.948782325, 1.37578589e-08, 1, -5.56731905e-08, -0.948782325, 3.06420738e-08, 0.315930545)
			elseif MYLEVEL == 950 or MYLEVEL <= 974 then
			Ms = "Zombie [Lv. 950]"
			NameQuest = "ZombieQuest"
			QuestLv = 1
			NameQ = "Zombie"
			CFrameQ = CFrame.new(-5492.79395, 48.5151672, -793.710571, 0.321800292, -6.24695815e-08, 0.946807742, 4.05616092e-08, 1, 5.21931227e-08, -0.946807742, 2.16082796e-08, 0.321800292)
			CFramePuk = CFrame.new(-5736.03516, 126.031998, -728.026184, 0.0818082988, -5.90035434e-08, 0.996648133, 3.5947787e-09, 1, 5.89069167e-08, -0.996648133, -1.23634614e-09, 0.0818082988)
			elseif MYLEVEL == 975 or MYLEVEL <= 999 then
			Ms = "Vampire [Lv. 975]"
			NameQuest = "ZombieQuest"
			QuestLv = 2
			NameQ = "Vampire"
			CFrameQ = CFrame.new(-5492.79395, 48.5151672, -793.710571, 0.321800292, -6.24695815e-08, 0.946807742, 4.05616092e-08, 1, 5.21931227e-08, -0.946807742, 2.16082796e-08, 0.321800292)
			CFramePuk = CFrame.new(-6028.23584, 6.40270138, -1295.4563, 0.667547405, 0, 0.744567394, -0, 1.00000012, -0, -0.744567394, 0, 0.667547405)
			elseif MYLEVEL == 1000 or MYLEVEL <= 1049 then
			Ms = "Snow Trooper [Lv. 1000]"
			NameQuest = "SnowMountainQuest"
			QuestLv = 1
			NameQ = "Snow Trooper"
			CFrameQ = CFrame.new(605.670532, 401.422028, -5370.10107, 0.459257662, -9.56824509e-10, -0.888303101, 5.98925964e-10, 1, -7.67489405e-10, 0.888303101, -1.79552401e-10, 0.459257662)
			CFramePuk = CFrame.new(544.207947, 401.422028, -5309.08887, 0.503866196, -2.06684501e-08, 0.86378175, 1.27917943e-09, 1, 2.31816841e-08, -0.86378175, -1.05755351e-08, 0.503866196)
			elseif MYLEVEL == 1050 or MYLEVEL <= 1099 then
			Ms = "Winter Warrior [Lv. 1050]"
			NameQuest = "SnowMountainQuest"
			QuestLv = 2
			NameQ = "Winter Warrior"
			CFrameQ = CFrame.new(605.670532, 401.422028, -5370.10107, 0.459257662, -9.56824509e-10, -0.888303101, 5.98925964e-10, 1, -7.67489405e-10, 0.888303101, -1.79552401e-10, 0.459257662)
			CFramePuk = CFrame.new(1240.86279, 461.108154, -5191.104, 0.528719008, -7.18234645e-08, 0.848796904, 2.89169716e-10, 1, 8.44378363e-08, -0.848796904, -4.4398444e-08, 0.528719008)
			elseif MYLEVEL == 1100 or MYLEVEL <= 1124 then
			Ms = "Lab Subordinate [Lv. 1100]"
			NameQuest = "IceSideQuest"
			QuestLv = 1
			NameQ = "Lab Subordinate"
			CFrameQ = CFrame.new(-6060.10693, 15.9868021, -4904.7876, -0.411000341, -5.06538868e-07, 0.91163528, 1.26306062e-07, 1, 6.12581289e-07, -0.91163528, 3.66916197e-07, -0.411000341)
			CFramePuk = CFrame.new(-5833.63379, 48.4371948, -4510.4458, 0.0372838341, 5.56001822e-09, -0.999304712, -6.95599089e-09, 1, 5.30436006e-09, 0.999304712, 6.75338763e-09, 0.0372838341)
			elseif MYLEVEL == 1125 or MYLEVEL <= 1174 then
			Ms = "Horned Warrior [Lv. 1125]"
			NameQuest = "IceSideQuest"
			QuestLv = 2
			NameQ = "Horned Warrior"
			CFrameQ = CFrame.new(-6060.10693, 15.9868021, -4904.7876, -0.411000341, -5.06538868e-07, 0.91163528, 1.26306062e-07, 1, 6.12581289e-07, -0.91163528, 3.66916197e-07, -0.411000341)
			CFramePuk = CFrame.new(-6168.15918, 42.7079964, -6020.96826, -0.744210601, 2.41774178e-09, -0.667945027, -2.3336304e-09, 1, 6.21975493e-09, 0.667945027, 6.18754425e-09, -0.744210601)
			elseif MYLEVEL == 1175 or MYLEVEL <= 1199 then
			Ms = "Magma Ninja [Lv. 1175]"
			NameQuest = "FireSideQuest"
			QuestLv = 1
			NameQ = "Magma Ninja"
			CFrameQ = CFrame.new(-5429.68359, 15.9517593, -5296.70215, 0.919959962, -6.00166317e-08, -0.392012328, 2.29238974e-08, 1, -9.93018858e-08, 0.392012328, 8.23673076e-08, 0.919959962)
			CFramePuk = CFrame.new(-5404.85449, 22.8623676, -5896.09033, -0.519595861, 4.74720929e-09, 0.854412138, 1.52255595e-08, 1, 3.70304742e-09, -0.854412138, 1.49329917e-08, -0.519595861)
			if _G.Autofram and (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 500 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-5466.8896484375, 15.951756477356, -5212.197265625))
			end
			elseif MYLEVEL == 1200 or MYLEVEL <= 1249 then
			Ms = "Lava Pirate [Lv. 1200]"
			NameQuest = "FireSideQuest"
			QuestLv = 2
			NameQ = "Lava Pirate"
			CFrameQ = CFrame.new(-5429.68359, 15.9517593, -5296.70215, 0.919959962, -6.00166317e-08, -0.392012328, 2.29238974e-08, 1, -9.93018858e-08, 0.392012328, 8.23673076e-08, 0.919959962)
			CFramePuk = CFrame.new(-5075.1958, 16.1485081, -4814.36133, -0.800640523, -1.06090866e-07, 0.599145055, -6.59776447e-08, 1, 8.89041587e-08, -0.599145055, 3.16500923e-08, -0.800640523)
			elseif MYLEVEL == 1250 or MYLEVEL <= 1274 then
			Ms = "Ship Deckhand [Lv. 1250]"
			NameQuest = "ShipQuest1" 
			QuestLv = 1
			NameQ = "Ship Deckhand"
			CFrameQ = CFrame.new(1038.67456, 125.057098, 32911.3477, 0.120709591, 5.22710089e-08, -0.992687881, 7.9174507e-09, 1, 5.36187876e-08, 0.992687881, -1.43318593e-08, 0.120709591)
			CFramePuk = CFrame.new(1215.14063, 125.057114, 33050.7188, 0.527230442, 2.61814961e-08, 0.849722326, -5.66963045e-08, 1, 4.36674741e-09, -0.849722326, -5.04783984e-08, 0.527230442)
			if _G.Autofram and (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 20000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
			elseif MYLEVEL == 1275 or MYLEVEL <= 1299 then
			Ms = "Ship Engineer [Lv. 1275]"
			NameQuest = "ShipQuest1" 
			QuestLv = 2
			NameQ = "Ship Engineer"
			CFrameQ = CFrame.new(1038.67456, 125.057098, 32911.3477, 0.120709591, 5.22710089e-08, -0.992687881, 7.9174507e-09, 1, 5.36187876e-08, 0.992687881, -1.43318593e-08, 0.120709591)
			CFramePuk = CFrame.new(862.985413, 40.4428635, 32867.9492, -0.847809434, 8.49998827e-08, -0.530301034, 2.99658929e-08, 1, 1.1237865e-07, 0.530301034, 7.93847335e-08, -0.847809434)
			if _G.Autofram and (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 20000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
			elseif MYLEVEL == 1300 or MYLEVEL <= 1324 then
			Ms = "Ship Steward [Lv. 1300]"
			NameQuest = "ShipQuest2" 
			QuestLv = 1
			NameQ = "Ship Steward"
			CFrameQ = CFrame.new(969.268311, 125.057121, 33245.2695, -0.85863924, -4.77058464e-08, -0.512580395, -1.49134394e-08, 1, -6.80880134e-08, 0.512580395, -5.08187057e-08, -0.85863924)
			CFramePuk = CFrame.new(923.611511, 129.555984, 33442.3125, 0.997516274, 9.71936913e-08, 0.0704362914, -9.52239958e-08, 1, -3.13219992e-08, -0.0704362914, 2.45369804e-08, 0.997516274)
			if _G.Autofram and (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 20000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
			elseif MYLEVEL == 1325 or MYLEVEL <= 1349 then
			Ms = "Ship Officer [Lv. 1325]"
			NameQuest = "ShipQuest2" 
			QuestLv = 2
			NameQ = "Ship Officer"
			CFrameQ = CFrame.new(969.268311, 125.057121, 33245.2695, -0.85863924, -4.77058464e-08, -0.512580395, -1.49134394e-08, 1, -6.80880134e-08, 0.512580395, -5.08187057e-08, -0.85863924)
			CFramePuk = CFrame.new(882.275574, 181.057739, 33354.1797, 0.845816016, -3.71928088e-08, -0.533474684, 1.28583932e-09, 1, -6.7679359e-08, 0.533474684, 5.65583242e-08, 0.845816016)
			if _G.Autofram and (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 20000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
			end
			elseif MYLEVEL == 1350 or MYLEVEL <= 1374 then
			Ms = "Arctic Warrior [Lv. 1350]"
			NameQuest = "FrostQuest" 
			QuestLv = 1
			NameQ = "Arctic Warrior"
			CFrameQ = CFrame.new(5669.43506, 28.2117786, -6482.60107, 0.888092756, 1.02705066e-07, 0.459664226, -6.20391774e-08, 1, -1.03572376e-07, -0.459664226, 6.34646895e-08, 0.888092756)
			CFramePuk = CFrame.new(5995.9292, 57.0727844, -6184.98926, 0.706337512, 5.23128296e-09, -0.707875192, -2.2285974e-08, 1, -1.48474424e-08, 0.707875192, 2.62629936e-08, 0.706337512)
			if _G.Autofram and (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 20000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 89.034996032715, -132.83953857422))
			end
			elseif MYLEVEL == 1375 or MYLEVEL <= 1424 then
			Ms = "Snow Lurker [Lv. 1375]"
			NameQuest = "FrostQuest" 
			QuestLv = 2
			NameQ = "Snow Lurker"
			CFrameQ = CFrame.new(5669.43506, 28.2117786, -6482.60107, 0.888092756, 1.02705066e-07, 0.459664226, -6.20391774e-08, 1, -1.03572376e-07, -0.459664226, 6.34646895e-08, 0.888092756)
			CFramePuk = CFrame.new(5516.27539, 60.5209846, -6830.82764, 0.219563305, -7.8544824e-09, 0.975598276, 4.69439376e-09, 1, 6.99444236e-09, -0.975598276, 3.04411962e-09, 0.219563305)
			elseif MYLEVEL == 1425 or MYLEVEL <= 1449 then
			Ms = "Sea Soldier [Lv. 1425]"
			NameQuest = "ForgottenQuest" 
			QuestLv = 1
			NameQ = "Sea Soldier"
			CFrameQ = CFrame.new(-3053.97339, 236.846283, -10146.1484, -0.999963522, -2.10707256e-08, -0.00854360498, -2.09657198e-08, 1, -1.23802275e-08, 0.00854360498, -1.22006529e-08, -0.999963522)
			CFramePuk = CFrame.new(-3026.54834, 29.5403671, -9758.74316, -0.999909937, 1.71713896e-08, -0.0134194754, 1.68009748e-08, 1, 2.7715517e-08, 0.0134194754, 2.74875607e-08, -0.999909937)
			if _G.Autofram and (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 20000 then
				game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 89.034996032715, -132.83953857422))
			end
			elseif MYLEVEL >= 1450  then
			Ms = "Water Fighter [Lv. 1450]"
			NameQuest = "ForgottenQuest" 
			QuestLv = 2
			NameQ = "Water Fighter"
			CFrameQ = CFrame.new(-3053.97339, 236.846283, -10146.1484, -0.999963522, -2.10707256e-08, -0.00854360498, -2.09657198e-08, 1, -1.23802275e-08, 0.00854360498, -1.22006529e-08, -0.999963522)
			CFramePuk = CFrame.new(-3262.00098, 298.699615, -10553.6943, -0.233570755, -4.57538185e-08, 0.972339869, -5.80986068e-08, 1, 3.30992194e-08, -0.972339869, -4.87605725e-08, -0.233570755)
			end 
		end
		if world3 then
			magbring = 400
			if MYLEVEL == 1500 or MYLEVEL <= 1524 then
				Ms = "Pirate Millionaire [Lv. 1500]"
				NameQuest = "PiratePortQuest" 
				QuestLv = 1
				NameQ = "Pirate Millionaire"
				CFrameQ = CFrame.new(-288.688629, 43.7932091, 5578.0918, -0.980135322, 4.04644034e-08, 0.198329896, 5.16003063e-08, 1, 5.0980109e-08, -0.198329896, 6.02012875e-08, -0.980135322)
				CFramePuk = CFrame.new(-362.372589, 116.311394, 5690.42188, 0.982939184, -1.16153336e-08, -0.183930904, 1.35050096e-08, 1, 9.02115538e-09, 0.183930904, -1.13512355e-08, 0.982939184)
			elseif MYLEVEL == 1525 or MYLEVEL <= 1574 then
				Ms = "Pistol Billionaire [Lv. 1525]"
				NameQuest = "PiratePortQuest" 
				QuestLv = 2
				NameQ = "Pistol Billionaire"
				CFrameQ = CFrame.new(-288.688629, 43.7932091, 5578.0918, -0.980135322, 4.04644034e-08, 0.198329896, 5.16003063e-08, 1, 5.0980109e-08, -0.198329896, 6.02012875e-08, -0.980135322)
				CFramePuk = CFrame.new(-238.026596, 219.645935, 6007.1748, 0.902000248, -1.08513618e-07, -0.431735516, 9.17130407e-08, 1, -5.97320096e-08, 0.431735516, 1.42825076e-08, 0.902000248)
			elseif MYLEVEL == 1575 or MYLEVEL <= 1599 then
				Ms = "Dragon Crew Warrior [Lv. 1575]"
				NameQuest = "AmazonQuest" 
				QuestLv = 1
				NameQ = "Dragon Crew Warrior"
				CFrameQ = CFrame.new(5833.72559, 51.3513527, -1104.3147, -0.958539188, -3.53234562e-08, 0.284960806, -3.93179853e-08, 1, -8.29718783e-09, -0.284960806, -1.91572642e-08, -0.958539188)
				CFramePuk = CFrame.new(6210.00977, 51.4822731, -1187.48975, 0.208473638, 2.79291683e-08, -0.978027999, -6.3442954e-08, 1, 1.50332973e-08, 0.978027999, 5.89149387e-08, 0.208473638)
			elseif MYLEVEL == 1600 or MYLEVEL <= 1624 then
				Ms = "Dragon Crew Archer [Lv. 1600]"
				NameQuest = "AmazonQuest" 
				QuestLv = 2
				NameQ = "Dragon Crew Archer"
				CFrameQ = CFrame.new(5833.72559, 51.3513527, -1104.3147, -0.958539188, -3.53234562e-08, 0.284960806, -3.93179853e-08, 1, -8.29718783e-09, -0.284960806, -1.91572642e-08, -0.958539188)
				CFramePuk = CFrame.new(6672.1167, 386.634491, 102.138634, -0.879578114, 4.99873778e-08, 0.475754529, -1.44054524e-09, 1, -1.07732973e-07, -0.475754529, -9.54449106e-08, -0.879578114)
			elseif MYLEVEL == 1625 or MYLEVEL <= 1649 then
				Ms = "Female Islander [Lv. 1625]"
				NameQuest = "AmazonQuest2" 
				QuestLv = 1
				NameQ = "Female Islander"
				CFrameQ = CFrame.new(5445.99756, 601.603638, 750.611145, -0.0389447734, 1.17245778e-08, -0.999241352, 1.19459349e-08, 1, 1.12678942e-08, 0.999241352, -1.1498047e-08, -0.0389447734)
				CFramePuk = CFrame.new(4660.0293, 793.07666, 771.150757, -0.300044596, 6.91594604e-09, -0.953925192, -9.75659518e-08, 1, 3.79380722e-08, 0.953925192, 1.04453733e-07, -0.300044596)
			elseif MYLEVEL == 1650 or MYLEVEL <= 1699 then
				Ms = "Giant Islander [Lv. 1650]"
				NameQuest = "AmazonQuest2" 
				QuestLv = 2
				NameQ = "Giant Islander"
				CFrameQ = CFrame.new(5445.99756, 601.603638, 750.611145, -0.0389447734, 1.17245778e-08, -0.999241352, 1.19459349e-08, 1, 1.12678942e-08, 0.999241352, -1.1498047e-08, -0.0389447734)
				CFramePuk = CFrame.new(5013.77881, 664.0849, -42.7317543, 0.793121755, 2.98509946e-08, 0.609063148, -3.13217008e-08, 1, -8.22422486e-09, -0.609063148, -1.25540822e-08, 0.793121755)
			elseif MYLEVEL == 1700 or MYLEVEL <= 1724 then
				Ms = "Marine Commodore [Lv. 1700]"
				NameQuest = "MarineTreeIsland" 
				QuestLv = 1
				NameQ = "Marine Commodore"
				CFrameQ = CFrame.new(2179.58447, 28.7054367, -6738.48682, 0.97564882, -2.54533923e-08, -0.219338506, 1.31742075e-08, 1, -5.74454191e-08, 0.219338506, 5.31569455e-08, 0.97564882)
				CFramePuk = CFrame.new(2548.86279, 124.071259, -7774.8999, -0.790427029, -1.174846e-08, -0.612556159, -2.99833545e-08, 1, 1.95103667e-08, 0.612556159, 3.37880124e-08, -0.790427029)
			elseif MYLEVEL == 1725 or MYLEVEL <= 1774 then
				Ms = "Marine Rear Admiral [Lv. 1725]"
				NameQuest = "MarineTreeIsland" 
				QuestLv = 2
				NameQ = "Marine Rear Admiral"
				CFrameQ = CFrame.new(2179.58447, 28.7054367, -6738.48682, 0.97564882, -2.54533923e-08, -0.219338506, 1.31742075e-08, 1, -5.74454191e-08, 0.219338506, 5.31569455e-08, 0.97564882)
				CFramePuk = CFrame.new(3582.24365, 160.524048, -7055.01416, -0.182099551, 6.68982807e-08, -0.983280122, 8.52377937e-08, 1, 5.22501367e-08, 0.983280122, -7.42978941e-08, -0.182099551)
			elseif MYLEVEL == 1775 or MYLEVEL <= 1799 then
				Ms = "Fishman Raider [Lv. 1775]"
				NameQuest = "DeepForestIsland3" 
				QuestLv = 1
				NameQ = "Fishman Raider"
				CFrameQ = CFrame.new(-10582.666, 331.762634, -8758.61035, 0.919332206, 1.69593086e-08, -0.393482327, -3.42409479e-08, 1, -3.68999942e-08, 0.393482327, 4.73965578e-08, 0.919332206)
				CFramePuk = CFrame.new(-10449.9258, 331.762634, -8475.85742, -0.739984214, -8.96819241e-09, 0.67262423, -5.59647688e-08, 1, -4.82362239e-08, -0.67262423, -7.33373042e-08, -0.739984214)
			elseif MYLEVEL == 1800 or MYLEVEL <= 1824 then
				Ms = "Fishman Captain [Lv. 1800]"
				NameQuest = "DeepForestIsland3" 
				QuestLv = 2
				NameQ = "Fishman Captain"
				CFrameQ = CFrame.new(-10582.666, 331.762634, -8758.61035, 0.919332206, 1.69593086e-08, -0.393482327, -3.42409479e-08, 1, -3.68999942e-08, 0.393482327, 4.73965578e-08, 0.919332206)
				CFramePuk = CFrame.new(-11035.9189, 331.762634, -8966.12012, -0.199661195, 8.05780545e-08, -0.979865015, -2.36975328e-08, 1, 8.70625314e-08, 0.979865015, 4.06033926e-08, -0.199661195)
			elseif MYLEVEL == 1825 or MYLEVEL <= 1849 then
				Ms = "Forest Pirate [Lv. 1825]"
				NameQuest = "DeepForestIsland" 
				QuestLv = 1
				NameQ = "Forest Pirate"
				CFrameQ = CFrame.new(-13232.082, 332.378143, -7627.49121, -0.717027605, -4.07509866e-08, 0.69704479, 3.86317822e-08, 1, 9.8201788e-08, -0.69704479, 9.734147e-08, -0.717027605)
				CFramePuk = CFrame.new(-13438.9268, 417.009583, -7767.28467, -0.301585436, -7.02043721e-08, -0.953439176, -4.40521433e-08, 1, -5.96985004e-08, 0.953439176, 2.39968401e-08, -0.301585436)
			elseif MYLEVEL == 1850 or MYLEVEL <= 1899 then
				Ms = "Mythological Pirate [Lv. 1850]"
				NameQuest = "DeepForestIsland" 
				QuestLv = 2
				NameQ = "Mythological Pirate"
				CFrameQ = CFrame.new(-13232.082, 332.378143, -7627.49121, -0.717027605, -4.07509866e-08, 0.69704479, 3.86317822e-08, 1, 9.8201788e-08, -0.69704479, 9.734147e-08, -0.717027605)
				CFramePuk = CFrame.new(-13560.6543, 522.013672, -6733.91113, 0.996960402, -1.61884088e-08, 0.0779099241, 1.91753653e-08, 1, -3.75904605e-08, -0.0779099241, 3.89701533e-08, 0.996960402)
			elseif MYLEVEL == 1900 or MYLEVEL <= 1924 then
				Ms = "Jungle Pirate [Lv. 1900]"
				NameQuest = "DeepForestIsland2" 
				QuestLv = 1
				NameQ = "Jungle Pirate"
				CFrameQ = CFrame.new(-12683.9668, 390.860687, -9901.30176, 0.152271122, 4.28084199e-08, -0.988338768, -4.4882615e-08, 1, 3.63985464e-08, 0.988338768, 3.88167827e-08, 0.152271122)
				CFramePuk = CFrame.new(-11983.4141, 375.940613, -10459.2383, 0.999999106, 1.88226306e-08, 0.00133047614, -1.87607263e-08, 1, -4.65408618e-08, -0.00133047614, 4.65158578e-08, 0.999999106)
			elseif MYLEVEL == 1925 or MYLEVEL <= 1974 then
				Ms = "Musketeer Pirate [Lv. 1925]"
				NameQuest = "DeepForestIsland2" 
				QuestLv = 2
				NameQ = "Musketeer Pirate"
				CFrameQ = CFrame.new(-12683.9668, 390.860687, -9901.30176, 0.152271122, 4.28084199e-08, -0.988338768, -4.4882615e-08, 1, 3.63985464e-08, 0.988338768, 3.88167827e-08, 0.152271122)
				CFramePuk = CFrame.new(-13293.082, 520.447632, -9901.99316, -0.758020341, -6.61346249e-08, 0.652230918, -2.15839417e-08, 1, 7.63127872e-08, -0.652230918, 4.37689316e-08, -0.758020341)
			elseif MYLEVEL == 1975 or MYLEVEL <= 1999 then
				Ms = "Reborn Skeleton [Lv. 1975]"
				NameQuest = "HauntedQuest1" 
				QuestLv = 1
				NameQ = "Reborn Skeleton"
				CFrameQ = CFrame.new(-9481.97754, 142.104843, 5566.03662, 0.00151404156, -4.14115426e-08, -0.999998868, -3.46592838e-10, 1, -4.14121146e-08, 0.999998868, 4.092921e-10, 0.00151404156)
				CFramePuk = CFrame.new(-8762.2832, 185.188904, 6169.08057, 0.964605391, 2.60655728e-08, 0.263697594, -2.23583552e-08, 1, -1.70596284e-08, -0.263697594, 1.05599645e-08, 0.964605391)
			elseif MYLEVEL == 2000 or MYLEVEL <= 2024 then
				Ms = "Living Zombie [Lv. 2000]"
				NameQuest = "HauntedQuest1" 
				QuestLv = 2
				NameQ = "Living Zombie"
				CFrameQ = CFrame.new(-9481.97754, 142.104843, 5566.03662, 0.00151404156, -4.14115426e-08, -0.999998868, -3.46592838e-10, 1, -4.14121146e-08, 0.999998868, 4.092921e-10, 0.00151404156)
				CFramePuk = CFrame.new(-10081.085, 237.834961, 5913.92871, 0.0515871011, 9.59092787e-08, 0.998668492, 4.31864713e-08, 1, -9.82679822e-08, -0.998668492, 4.81983271e-08, 0.0515871011)
			elseif MYLEVEL == 2025 or MYLEVEL <= 2049 then
				Ms = "Demonic Soul [Lv. 2025]"
				NameQuest = "HauntedQuest2" 
				QuestLv = 1
				NameQ = "Demonic Soul"
				CFrameQ = CFrame.new(-9513.68945, 172.104813, 6078.30811, 0.06916935, 2.37454696e-08, 0.997604907, 1.21678923e-07, 1, -3.22391358e-08, -0.997604907, 1.23617454e-07, 0.06916935)
				CFramePuk = CFrame.new(-9661.06152, 234.989151, 6208.34473, 0.839007735, 1.00638069e-07, -0.544119537, -9.42643013e-08, 1, 3.9604533e-08, 0.544119537, 1.80625381e-08, 0.839007735)
			elseif MYLEVEL == 2050 or MYLEVEL <= 2074 then
				Ms = "Posessed Mummy [Lv. 2050]"
				NameQuest = "HauntedQuest2" 
				QuestLv = 2
				NameQ = "Posessed Mummy"
				CFrameQ = CFrame.new(-9513.68945, 172.104813, 6078.30811, 0.06916935, 2.37454696e-08, 0.997604907, 1.21678923e-07, 1, -3.22391358e-08, -0.997604907, 1.23617454e-07, 0.06916935)
				CFramePuk = CFrame.new(-9555.10254, 66.3880768, 6371.47021, 0.993915081, -2.2833456e-08, 0.110149056, 2.02630606e-08, 1, 2.44549945e-08, -0.110149056, -2.20742304e-08, 0.993915081)
			elseif MYLEVEL == 2075 or MYLEVEL <= 2099 then
				Ms = "Peanut Scout [Lv. 2075]"
				NameQuest = "NutsIslandQuest" 
				QuestLv = 1
				NameQ = "Peanut Scout"
				CFrameQ = CFrame.new(-2103.03442, 38.103981, -10192.5801, 0.779485822, -2.70350977e-08, 0.626419842, -3.08562882e-08, 1, 8.15541483e-08, -0.626419842, -8.2899291e-08, 0.779485822)
				CFramePuk = CFrame.new(-2149.84937, 122.471855, -10359.0498, -0.0922852308, -3.50682292e-08, -0.995732605, 3.04092396e-09, 1, -3.55003564e-08, 0.995732605, -6.30410568e-09, -0.0922852308)
			elseif MYLEVEL == 2100 or MYLEVEL <= 2124 then
				Ms = "Peanut President [Lv. 2100]"
				NameQuest = "NutsIslandQuest" 
				QuestLv = 2
				NameQ = "Peanut President"
				CFrameQ = CFrame.new(-2103.03442, 38.103981, -10192.5801, 0.779485822, -2.70350977e-08, 0.626419842, -3.08562882e-08, 1, 8.15541483e-08, -0.626419842, -8.2899291e-08, 0.779485822)
				CFramePuk = CFrame.new(-2149.84937, 122.471855, -10359.0498, -0.0922852308, -3.50682292e-08, -0.995732605, 3.04092396e-09, 1, -3.55003564e-08, 0.995732605, -6.30410568e-09, -0.0922852308)
			elseif MYLEVEL == 2125 or MYLEVEL <= 2149 then
				Ms = "Ice Cream Chef [Lv. 2125]"
				NameQuest = "IceCreamIslandQuest" 
				QuestLv = 1
				NameQ = "Ice Cream Chef"
				CFrameQ = CFrame.new(-823.195129, 65.8453369, -10963.583, 0.367210746, -2.2831804e-08, -0.930137753, 2.00119876e-09, 1, -2.37566322e-08, 0.930137753, 6.86230051e-09, 0.367210746)
				CFramePuk = CFrame.new(-846.166931, 205.853973, -11006.5137, -0.153710946, 3.34348504e-09, 0.988115847, -4.13023145e-08, 1, -9.80867032e-09, -0.988115847, -4.23191722e-08, -0.153710946)
			elseif MYLEVEL == 2150 or MYLEVEL <= 2199 then
				Ms = "Ice Cream Commander [Lv. 2150]"
				NameQuest = "IceCreamIslandQuest" 
				QuestLv = 2
				NameQ = "Ice Cream Commander"
				CFrameQ = CFrame.new(-823.195129, 65.8453369, -10963.583, 0.367210746, -2.2831804e-08, -0.930137753, 2.00119876e-09, 1, -2.37566322e-08, 0.930137753, 6.86230051e-09, 0.367210746)
				CFramePuk = CFrame.new(-846.166931, 205.853973, -11006.5137, -0.153710946, 3.34348504e-09, 0.988115847, -4.13023145e-08, 1, -9.80867032e-09, -0.988115847, -4.23191722e-08, -0.153710946)
			elseif MYLEVEL == 2200 or MYLEVEL <= 2224 then
				Ms = "Cookie Crafter [Lv. 2200]"
				NameQuest = "CakeQuest1" 
				QuestLv = 1
				NameQ = "Cookie Crafter"
				CFrameQ = CFrame.new(-2021.3193359375, 37.82402038574219, -12027.6845703125)
				CFramePuk = CFrame.new(-2288.84717, 93.943161, -12046.7285, 0.0389619507, -8.05070766e-09, 0.999240696, 1.44159458e-08, 1, 7.49472484e-09, -0.999240696, 1.41129908e-08, 0.0389619507)
			elseif MYLEVEL == 2225 or MYLEVEL <= 2249 then
				Ms = "Cake Guard [Lv. 2225]"
				NameQuest = "CakeQuest1" 
				QuestLv = 2
				NameQ = "Cake Guard"
				CFrameQ = CFrame.new(-2021.3193359375, 37.82402038574219, -12027.6845703125)
				CFramePuk = CFrame.new(-1600.24854, 195.694992, -12346.0342, -0.9457618, -7.09395209e-08, -0.32486099, -9.57561568e-08, 1, 6.04042683e-08, 0.32486099, 8.82354882e-08, -0.9457618)
			elseif MYLEVEL == 2250 or MYLEVEL <= 2274 then
				Ms = "Baking Staff [Lv. 2250]"
				NameQuest = "CakeQuest2" 
				QuestLv = 1
				NameQ = "Baking Staff"
				CFrameQ = CFrame.new(-1928.67395, 37.8331604, -12842.3936, -0.235107109, -7.40617239e-08, -0.971969485, -7.00571334e-08, 1, -5.92516507e-08, 0.971969485, 5.41629106e-08, -0.235107109)
				CFramePuk = CFrame.new(-1848.26746, 186.937271, -13007.0479, 0.460077673, 6.23081897e-09, -0.887878656, -9.55947232e-09, 1, 2.06415507e-09, 0.887878656, 7.53797913e-09, 0.460077673)
			elseif MYLEVEL >= 2275 then
				Ms = "Head Baker [Lv. 2275]"
				NameQuest = "CakeQuest2" 
				QuestLv = 2
				NameQ = "Head Baker"
				CFrameQ = CFrame.new(-1928.67395, 37.8331604, -12842.3936, -0.235107109, -7.40617239e-08, -0.971969485, -7.00571334e-08, 1, -5.92516507e-08, 0.971969485, 5.41629106e-08, -0.235107109)
				CFramePuk = CFrame.new(-2012.3689, 177.257675, -12839.6357, 0.759093106, 4.20168478e-09, -0.650982082, 1.84710747e-10, 1, 6.66976474e-09, 0.650982082, -5.18321563e-09, 0.759093106)  
		end
   	end
end

checklevel()

function bypasstp(x)
    spawn(function()
		game.Players.localPlayer.Character:WaitForChild('HumanoidRootPart').CFrame = x
		task.wait(0.5)
        game.Players.LocalPlayer.Character.Head:Destroy()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
    end)
end

function equip(Itme)
	if  game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(Itme) then
		getgenv().Itmes =  game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(Itme)
		wait(.1)
		game.Players.LocalPlayer.Character.Humanoid:EquipTool(Itmes)
	end
	end

function doingquest() --- checkquest
   return(game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible)
end




posrandom = 0


function AutoEquiedHat() 
    hasHat = false
    for i, v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do 
        if v:IsA('Tool') then 
            if v.ToolTip == "Wear" then 
                hat = v.Name
            end
        end
    end
    for i, v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do 
        if v:IsA('Tool') then 
            if v.ToolTip == "Wear" then 
                hat = v.Name
            end
        end
    end
    for i, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
        if v.ClassName == 'Accessory' then
            if v:FindFirstChild('IsAccessory') then
                hasHat = true
            end
        end
    end
    if not hasHat then
            if hat then
        repeat wait()
            game.Players.LocalPlayer.Character.Humanoid:EquipTool(game.Players.LocalPlayer.Backpack:FindFirstChild(hat))
        until not game.Players.LocalPlayer.Backpack:FindFirstChild(hat)
        if game.Players.LocalPlayer.Character:FindFirstChild(hat) then 
            hatUse = game.Players.LocalPlayer.Character:FindFirstChild(hat)
            hatUse.RemoteFunction:InvokeServer()
        end
     end
    end
end

spawn(function()---new autofarm
   while task.wait() do
       pcall(function()
           if _G.Autofram then
                  if game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == false then
					checklevel()
						   task.wait()
						   checklevel()
							task.wait()
							UseFast = false
							if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - CFrameQ.Position).Magnitude <= 2500 then
								two(CFrameQ)
							else
								wait(1)
								bypasstp(CFrameQ)
								if game.Players.LocalPlayer.Character.Humanoid.Health <= 0 then
									tween:Cancel()
								end
								tween:Cancel()
							end
                          	game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                           	local distance_Quest = (CFrameQ.Position - game.Players.localPlayer.Character.HumanoidRootPart.Position).Magnitude 
							if distance_Quest <= 5 then
								wait(.5)
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
								if game.Players.LocalPlayer.Character.Humanoid.Health <= 0 then
									tween:Cancel()
								else
									local Quest = (CFrameQ.Position - game.Players.localPlayer.Character.HumanoidRootPart.Position).Magnitude 
									if Quest <= 5 then
										wait(game.ReplicatedStorage.Remotes.CommF_:InvokeServer('StartQuest', NameQuest, QuestLv))
									else
										two(CFrameQ)
									end
								end
							else
								two(CFrameQ)
							end
                  elseif game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                           checklevel()
						   AutoEquiedHat()
                           if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
                            checklevel()
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                checklevel()
                                if v.Name == Ms and v:FindFirstChild("Humanoid") then
                                    checklevel()
                                    if v.Humanoid.Health > 0 then
                                        checklevel()
                                        repeat wait()
											if not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,NameQ) then
												local Quest = (CFrameQ.Position - game.Players.localPlayer.Character.HumanoidRootPart.Position).Magnitude 
												if Quest <= 5 then
													wait(game.ReplicatedStorage.Remotes.CommF_:InvokeServer('StartQuest', NameQuest, QuestLv))
												else
													two(CFrameQ)
												end
											end
                                            if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,NameQ) then
                                             checklevel()
                                             if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
                                                 checklevel()
                                                 _groupMon = true
                                                 
                                                 equip(_G.SelectWeapon)
                                                if not game.Players.LocalPlayer.Character:FindFirstChild('HasBuso')then
                                                   game.ReplicatedStorage.Remotes.CommF_:InvokeServer('Buso')
                                                end
												if game.Players.LocalPlayer.Character.Humanoid.Health <= 0 then
													tween:Cancel()
		
												else
													UseFast = true
													two(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
												end
                                                 PosMon = v.HumanoidRootPart.CFrame
                                                 v.Humanoid.JumpPower = 0
                                                 v.Humanoid.WalkSpeed = 0
                                                 v.Humanoid.Sit = true
                                                 v.HumanoidRootPart.CanCollide = false
                                                 v.Humanoid:ChangeState(14)
                                                 sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
                                               
                                                 
                                             end
                                            end
                                        until not v.Parent or v.Humanoid.Health <= 0 or _G.Autofram == false or game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                        _groupMon = false
                                        checklevel()
                                    end
                                end
                            end
						else
							local QuestTitle = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text
							local ReplicatedStorage = game:GetService("ReplicatedStorage")
							local EnemieWorkspace = game:GetService("Workspace").Enemies
							if not EnemieWorkspace:FindFirstChild(Ms) and ReplicatedStorage:FindFirstChild(Ms) then
								bypasstp(ReplicatedStorage:FindFirstChild(Ms).HumanoidRootPart.CFrame * CFrame.new(0 , 75 , -75))
								if game.Players.LocalPlayer.Character.Humanoid.Health <= 0 then
									tween:Cancel()
								end
							end
							if not string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, NameQ) then
								local args = {
									[1] = "AbandonQuest"
								}
								game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
							end
					 _groupMon = false
                    end
               end
           end
       end)
   end
end)


spawn(function()
    game:GetService("RunService").Heartbeat:Connect(function()
        if getgenv().noclip or _G.A or _statetp  then
        if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Humanoid") then
            setfflag("HumanoidParallelRemoveNoPhysics", "False")
            setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
            game:GetService("Players").LocalPlayer.Character.Humanoid:ChangeState(11)
            end
        end
    end)
end)
-- spawn(function() 
--     while wait () do
--         pcall(function () 
--          local UpperTorso = game.Players.LocalPlayer.Character.UpperTorso
--         if getgenv().noclip or _G.A or _statetp then
--             if UseTween then
--                 if not  game.Players.LocalPlayer.Character.Humanoid.PlatformStand then
--                     game.Players.LocalPlayer.Character.Humanoid.PlatformStand = true
--                 end
--             else
--                 if game.Players.LocalPlayer.Character.Humanoid.PlatformStand then
--                     game.Players.LocalPlayer.Character.Humanoid.PlatformStand = false
--                 end
--             end
--             if not UpperTorso:FindFirstChild('BodyVelocity_Volkthan') then
--                 local BodyVelocity = Instance.new("BodyVelocity", UpperTorso)
--                 BodyVelocity.Name = 'BodyVelocity_Volkthan'
--                 BodyVelocity.Velocity = Vector3.new(0,0.1,0)
--                 BodyVelocity.MaxForce = Vector3.new(9e9, 9e9, 9e9)
--             end
--             if not UpperTorso:FindFirstChild('BodyGyro_Volkthan') then
--                 local BodyGyro = Instance.new("BodyGyro", UpperTorso)
--                 BodyGyro.Name = 'BodyGyro_Volkthan'
--                 BodyGyro.P = 9e4
--                 BodyGyro.MaxTorque = Vector3.new(9e9, 9e9, 9e9)
--                 BodyGyro.CFrame = UpperTorso.CFrame
--             end
--         else
--             if  UpperTorso:FindFirstChild('BodyVelocity_Volkthan') then
--                 UpperTorso:FindFirstChild('BodyVelocity_Volkthan'):Destroy()
--             end
--             if  UpperTorso:FindFirstChild('BodyGyro_Volkthan') then
--                 UpperTorso:FindFirstChild('BodyGyro_Volkthan'):Destroy()
--             end
--         end    
--         end)
--     end
-- end)





-- -- -- spawn(function()
-- -- -- 	pcall(function()
-- -- -- 		game:GetService("RunService").Heartbeat:Connect(function()
-- -- -- 			if getgenv().noclip or _G.A or _statetp then
-- -- -- 				if not game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
-- -- -- 					local Noclip = Instance.new("BodyVelocity")
-- -- -- 					Noclip.Name = "BodyClip"
-- -- -- 					Noclip.Parent = game.Players.LocalPlayer.Character.HumanoidRootPart
-- -- -- 					Noclip.MaxForce = Vector3.new(100000,100000,100000)
-- -- -- 					Noclip.Velocity = Vector3.new(0,0,0)
-- -- -- 				end
-- -- -- 			else
-- -- -- 				if game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip") then
-- -- -- 					game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("BodyClip"):Destroy()
-- -- -- 				end
-- -- -- 			end
-- -- -- 		end)
-- -- -- 	end)
-- -- -- end)
local old = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework) 
local com = getupvalue(old,2)
require(game.ReplicatedStorage.Util.CameraShaker):Stop()

local CombatFramework = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
local Camera = require(game.ReplicatedStorage.Util.CameraShaker)
local Attack = 0.1
local backup = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
local Crit = getupvalues(backup)[2]
local CombatFrameworkR = getupvalues(backup)[2]
local CameraShakerR = require(game.ReplicatedStorage.Util.CameraShaker)
local plr = game.Players.LocalPlayer
local CbFw = debug.getupvalues(require(plr.PlayerScripts.CombatFramework))
local CbFw2 = CbFw[2]
function maxincrement()
	return #Crit.activeController.anims.basic
end
spawn(function()
    local old
    old = hookmetamethod(game, "__namecall",function(self,...)
        local method = getnamecallmethod() local args = {...}

        if method:lower() == "fireserver" then
            if args[1] == "hit" then
                args[3] = maxincrement()
                return old(self,unpack(args))
            end end
        return old(self,...)
	end) 
end)
do
    CameraShakerR:Stop()
end
function GetCurrentBlade() 
    local p13 = CbFw2.activeController
    local ret = p13.blades[1]
    if not ret then return end
    while ret.Parent~=game.Players.LocalPlayer.Character do ret=ret.Parent end
    return ret
end
function AttackNoCD() 
    local AC = CbFw2.activeController
    for i = 1, 1 do 
        local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
            plr.Character,
            {plr.Character.HumanoidRootPart},
            60
        )
        local cac = {}
        local hash = {}
        for k, v in pairs(bladehit) do
            if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then
                table.insert(cac, v.Parent.HumanoidRootPart)
                hash[v.Parent] = true
            end
        end
        bladehit = cac
        if #bladehit > 0 then
            local u8 = debug.getupvalue(AC.attack, 5)
            local u9 = debug.getupvalue(AC.attack, 6)
            local u7 = debug.getupvalue(AC.attack, 4)
            local u10 = debug.getupvalue(AC.attack, 7)
            local u12 = (u8 * 798405 + u7 * 727595) % u9
            local u13 = u7 * 798405
            (function()
                u12 = (u12 * u9 + u13) % 1099511627776
                u8 = math.floor(u12 / u9)
                u7 = u12 - u8 * u9
            end)()
            u10 = u10 + 1
            debug.setupvalue(AC.attack, 5, u8)
            debug.setupvalue(AC.attack, 6, u9)
            debug.setupvalue(AC.attack, 4, u7)
            debug.setupvalue(AC.attack, 7, u10)
            pcall(function()
                for k, v in pairs(AC.animator.anims.basic) do
                    v:Play()
                end                  
            end)
            if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] then 
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
                game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, i, "") 
            end
        end
    end
end

spawn(function()
    game:GetService("RunService").Stepped:Connect(function()
        pcall(function()
            com.activeController.hitboxMagnitude = 60
            if Nahee then
                    com.activeController.hitboxMagnitude = 60
                    com.activeController.active = false
                    com.activeController.blocking = false
                    com.activeController.focusStart = 0 
                    com.activeController.hitSound = nil
                    com.activeController.increment = 0 
                    com.activeController.timeToNextAttack = 0 
                    com.activeController.timeToNextBlock = 0 
                    com.activeController:attack()
            end
        end)
    end)
end)
cal = wait

spawn(function ()
    while cal() do
        if UseFast then
            pcall(function() 
                AttackNoCD()
            end)
        end
    end
end)

spawn(function() 
    while wait () do
        pcall(function () 
        local UpperTorso = game.Players.LocalPlayer.Character.UpperTorso
        if getgenv().noclip then
            if UseTween then
                if not  game.Players.LocalPlayer.Character.Humanoid.PlatformStand then
                    game.Players.LocalPlayer.Character.Humanoid.PlatformStand = true
                end
            else
                if game.Players.LocalPlayer.Character.Humanoid.PlatformStand then
                    game.Players.LocalPlayer.Character.Humanoid.PlatformStand = false
                end
            end
            if not UpperTorso:FindFirstChild('BodyVelocity_Volkthan') then
                local BodyVelocity = Instance.new("BodyVelocity", UpperTorso)
                BodyVelocity.Name = 'BodyVelocity_Volkthan'
                BodyVelocity.Velocity = Vector3.new(0,0.1,0)
                BodyVelocity.MaxForce = Vector3.new(9e9, 9e9, 9e9)
            end
            if not UpperTorso:FindFirstChild('BodyGyro_Volkthan') then
                local BodyGyro = Instance.new("BodyGyro", UpperTorso)
                BodyGyro.Name = 'BodyGyro_Volkthan'
                BodyGyro.P = 9e4
                BodyGyro.MaxTorque = Vector3.new(9e9, 9e9, 9e9)
                BodyGyro.CFrame = UpperTorso.CFrame
            end
        else
            if  UpperTorso:FindFirstChild('BodyVelocity_Volkthan') then
                UpperTorso:FindFirstChild('BodyVelocity_Volkthan'):Destroy()
            end
            if  UpperTorso:FindFirstChild('BodyGyro_Volkthan') then
                UpperTorso:FindFirstChild('BodyGyro_Volkthan'):Destroy()
            end
        end    
        end)
    end
end)


-- -- -- -- -- -- -- -- -- -- spawn(function()
-- -- -- -- -- -- -- -- -- -- 	while game:GetService("RunService").Stepped:wait(10) do
-- -- -- -- -- -- -- -- -- -- 		character = game.Players.LocalPlayer.Character 
-- -- -- -- -- -- -- -- -- -- 		if getgenv().noclip or _G.A then
-- -- -- -- -- -- -- -- -- -- 			pcall(function()
-- -- -- -- -- -- -- -- -- -- 				for _, v in pairs(character:GetDescendants()) do
-- -- -- -- -- -- -- -- -- -- 					pcall(function()
-- -- -- -- -- -- -- -- -- -- 						if v:IsA("BasePart") then
-- -- -- -- -- -- -- -- -- -- 							pcall(function()
-- -- -- -- -- -- -- -- -- -- 							v.CanCollide = false
-- -- -- -- -- -- -- -- -- -- 							end)
-- -- -- -- -- -- -- -- -- -- 						end
-- -- -- -- -- -- -- -- -- -- 					end)
-- -- -- -- -- -- -- -- -- -- 				end
-- -- -- -- -- -- -- -- -- -- 			end)
-- -- -- -- -- -- -- -- -- -- 		end
-- -- -- -- -- -- -- -- -- -- 	end
-- -- -- -- -- -- -- -- -- -- end)
local VirtualUser = game:GetService('VirtualUser')
spawn(function()---------- anti afk
    game:GetService("Players").LocalPlayer.Idled:connect(function()
        pcall(function()
            VirtualUser:Button2Down(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
            task.wait(1)
            VirtualUser:Button2Up(Vector2.new(0,0),workspace.CurrentCamera.CFrame)
        end)
    end)
end)

_groupMon = false

-- spawn(function()---- group mon
--     game:GetService("RunService").Heartbeat:Connect(function()
--         pcall(function()
--             if (_G.Autofram) and _groupMon then
--                 checklevel()
--                 for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
--                     if v.Name == Ms and (v.HumanoidRootPart.Position-PosMon.Position).magnitude <= 250 then --370
--                         if syn then
--                         v.HumanoidRootPart.CFrame = PosMon
--                         v.Humanoid.JumpPower = 0
--                         v.Humanoid.WalkSpeed = 0
--                         v.Humanoid.Sit = true
--                         v.HumanoidRootPart.CanCollide = false
--                         if v.Humanoid:FindFirstChild("Animator") then
--                             v.Humanoid.Animator:Destroy()
--                         end
--                         sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
--                         v.Humanoid:ChangeState(14)
--                         v.Humanoid:ChangeState(11)
--                     else
--                         v.HumanoidRootPart.CFrame = PosMon
--                         v.Humanoid.JumpPower = 0
--                         v.Humanoid.WalkSpeed = 0
--                         v.Humanoid.Sit = true
--                         v.HumanoidRootPart.CanCollide = false
--                         if v.Humanoid:FindFirstChild("Animator") then
--                             v.Humanoid.Animator:Destroy()
--                         end
--                         sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
--                         v.Humanoid:ChangeState(14)
--                         v.Humanoid:ChangeState(11)
--                         end
--                     end
--                 end
--             end
--         end)
--     end)
-- end)

spawn(function()---- group mon
    game:GetService("RunService").Heartbeat:Connect(function()
        pcall(function()
            if (_G.Autofram) and _groupMon then
                checklevel()
                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
					if v.Name == Ms then
						if v.Name == "Factory Staff [Lv. 800]" or v.Name == "God's Guard [Lv. 450]" or v.Name == "Vampire [Lv. 975]" or v.Name == 'Snow Trooper [Lv. 1000]' then
							if (v.HumanoidRootPart.Position - PosMon.Position).Magnitude <= 250 then
							v.Head.CanCollide = false
							v.Humanoid.Sit = false
							v.HumanoidRootPart.CanCollide = false
							v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
							v.HumanoidRootPart.CFrame = PosMon
							sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
							end
						else
							if (v.HumanoidRootPart.Position - PosMon.Position).Magnitude <= 350 then
						
								v.Head.CanCollide = false
								v.HumanoidRootPart.CanCollide = false
								v.Humanoid.Sit = false
								v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
								v.HumanoidRootPart.CFrame = PosMon
								sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
							-- end
							end
						end
					end
                end
            end
        end)
    end)
end)

function toTarget(targetPos, targetCFrame)
    if FastTween then
        Distance = (targetPos - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).Magnitude
        if Distance < 1000 then
            Speed = 325
        elseif Distance >= 1000 then
            Speed = 300
        end
    else
        Distance = (targetPos - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).Magnitude
        if Distance < 1000 then
            Speed = 275
        elseif Distance >= 1000 then
            Speed = 250
        end
    end
    local tweenfunc = {}

    local tween_s = game:service"TweenService"
    local info = TweenInfo.new((targetPos - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).Magnitude/Speed, Enum.EasingStyle.Linear)
    local tween = tween_s:Create(game:GetService("Players").LocalPlayer.Character["HumanoidRootPart"], info, {CFrame = targetCFrame * CFrame.fromAxisAngle(Vector3.new(1,0,0), math.rad(0))})
    tween:Play()

    function tweenfunc:Stop()
        tween:Cancel()
    end 

    if StatsBypass == "Bypassed" and UseTP then
        tween:Cancel()
        game:GetService("Players").LocalPlayer.Character["HumanoidRootPart"].CFrame = targetCFrame
    end
    if not tween then return tween end
    return tweenfunc
end





spawn(function()
    while wait() do
        if AutoSaber then
            _G.Autofram = false
            if game.Players.localPlayer.Data.Level.Value < 200 then
            else
                if game.Workspace.Map.Jungle.Final.Part.CanCollide == false then
                    if game.Workspace.Enemies:FindFirstChild("Saber Expert [Lv. 200] [Boss]") then
                        for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                            if v.Name == "Saber Expert [Lv. 200] [Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                repeat wait()
                                    if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
                                        Farmtween = toTarget(v.HumanoidRootPart.Position,v.HumanoidRootPart.CFrame)
                                    elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                        if Farmtween then
                                            Farmtween:Stop()
                                        end
                                        equip(_G.SelectWeapon)
                                        
                                        if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                                            local args = {
                                                [1] = "Buso"
                                            }
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                        end
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 10, 10)
                                        Click()
                                    end
                                until not AutoSaber or not v.Parent or v.Humanoid.Health <= 0
                               
                            end
                        end
                    else
                        Questtween = toTarget(CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position,CFrame.new(-1405.41956, 29.8519993, 5.62435055))
                        if (CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                            if Questtween then
                                Questtween:Stop()
                            end
                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1405.41956, 29.8519993, 5.62435055, 0.885240912, 3.52892613e-08, 0.465132833, -6.60881128e-09, 1, -6.32913171e-08, -0.465132833, 5.29540891e-08, 0.885240912)
                        end
                    end
                elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Relic") or game.Players.LocalPlayer.Character:FindFirstChild("Relic") and game.Players.localPlayer.Data.Level.Value >= 200 then
                    equip("Relic")
                    wait(0.5)
                    Questtween = toTarget(CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position,CFrame.new(-1405.41956, 29.8519993, 5.62435055))
                    if (CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                        if Questtween then
                            Questtween:Stop()
                        end
                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1405.41956, 29.8519993, 5.62435055, 0.885240912, 3.52892613e-08, 0.465132833, -6.60881128e-09, 1, -6.32913171e-08, -0.465132833, 5.29540891e-08, 0.885240912)
                    end
                else
                    if Workspace.Map.Jungle.QuestPlates.Door.CanCollide == false then
                        if game.Workspace.Map.Desert.Burn.Part.CanCollide == false then
                            if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan") == 0 then
                                if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 0 then
                                    if game.Workspace.Enemies:FindFirstChild("Mob Leader [Lv. 120] [Boss]") then
                                        for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                            if AutoSaber and v:IsA("Model") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 and v.Name == "Mob Leader [Lv. 120] [Boss]" then
                                                repeat
                                                    pcall(function() wait() 
                                                        if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
                                                            Farmtween = toTarget(v.HumanoidRootPart.Position,v.HumanoidRootPart.CFrame)
                                                        elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                            
                                                            equip(_G.SelectWeapon)
                                                            
                                                            if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
                                                                local args = {
                                                                    [1] = "Buso"
                                                                }
                                                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                                            end
                                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 10, 10)
                                                            Click()
                                                        end
                                                    end)
                                                until not AutoSaber or not v.Parent or v.Humanoid.Health <= 0
                                                
                                            end
                                        end
                                    else
                                        Questtween = toTarget(CFrame.new(-2848.59399, 7.4272871, 5342.44043).Position,CFrame.new(-2848.59399, 7.4272871, 5342.44043))
                                        if (CFrame.new(-2848.59399, 7.4272871, 5342.44043).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                            if Questtween then
                                                Questtween:Stop()
                                            end
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2848.59399, 7.4272871, 5342.44043, -0.928248107, -8.7248246e-08, 0.371961564, -7.61816636e-08, 1, 4.44474857e-08, -0.371961564, 1.29216433e-08, -0.928248107)
                                        end
                                    end
                                elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 1 then
                                    if game.Players.LocalPlayer.Backpack:FindFirstChild("Relic") or game.Players.LocalPlayer.Character:FindFirstChild("Relic") then
                                        equip("Relic")
                                        wait(0.5)
                                        Questtween = toTarget(CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position,CFrame.new(-1405.41956, 29.8519993, 5.62435055))
                                        if (CFrame.new(-1405.41956, 29.8519993, 5.62435055).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                            if Questtween then
                                                Questtween:Stop()
                                            end
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1405.41956, 29.8519993, 5.62435055)
                                        end
                                    else
                                        Questtween = toTarget(CFrame.new(-910.979736, 13.7520342, 4078.14624).Position,CFrame.new(-910.979736, 13.7520342, 4078.14624))
                                        if (CFrame.new(-910.979736, 13.7520342, 4078.14624).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                            if Questtween then
                                                Questtween:Stop()
                                            end
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-910.979736, 13.7520342, 4078.14624, 0.00685182028, -1.53155766e-09, -0.999976516, 9.15205245e-09, 1, -1.46888401e-09, 0.999976516, -9.14177267e-09, 0.00685182028)
                                            wait(.5)
                                            local args = {
                                                [1] = "ProQuestProgress",
                                                [2] = "RichSon"
                                            }
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                        end
                                    end
                                else
                                    Questtween = toTarget(CFrame.new(-910.979736, 13.7520342, 4078.14624).Position,CFrame.new(-910.979736, 13.7520342, 4078.14624))
                                    if (CFrame.new(-910.979736, 13.7520342, 4078.14624).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                        if Questtween then
                                            Questtween:Stop()
                                        end
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-910.979736, 13.7520342, 4078.14624)
                                        local args = {
                                            [1] = "ProQuestProgress",
                                            [2] = "RichSon"
                                        }
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                    end
                                end
                            else
                                if game.Players.LocalPlayer.Backpack:FindFirstChild("Cup") or game.Players.LocalPlayer.Character:FindFirstChild("Cup") then
                                    equip("Cup")
                                    if game.Players.LocalPlayer.Character.Cup.Handle:FindFirstChild("TouchInterest") then
                                        Questtween = toTarget(CFrame.new(1397.229, 37.3480148, -1320.85217).Position,CFrame.new(1397.229, 37.3480148, -1320.85217))
                                        if (CFrame.new(1397.229, 37.3480148, -1320.85217).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                            if Questtween then
                                                Questtween:Stop()
                                            end
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1397.229, 37.3480148, -1320.85217, -0.11285457, 2.01368788e-08, 0.993611455, 1.91641178e-07, 1, 1.50028845e-09, -0.993611455, 1.90586206e-07, -0.11285457)
                                        end
                                    else
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1458.54285, 88.2521744, -1390.34912, -0.00596274994, 1.13679788e-09, -0.999982238, 7.28181793e-10, 1, 1.132476e-09, 0.999982238, -7.21416205e-10, -0.00596274994)
                                        wait(0.5)
                                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan") ~= 0 then
                                            local args = {
                                                [1] = "ProQuestProgress",
                                                [2] = "SickMan"
                                            }
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                        end
                                    end
                                else
                                    Questtween = toTarget(game.Workspace.Map.Desert.Cup.Position,game.Workspace.Map.Desert.Cup.CFrame)
                                    if (game.Workspace.Map.Desert.Cup.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                        if Questtween then
                                            Questtween:Stop()
                                        end
                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Workspace.Map.Desert.Cup.CFrame
                                    end
                                    -- firetouchinterest(game.Workspace.Map.Desert.Cup.TouchInterest,game.Players.LocalPlayer.Character.Head, 1)
                                end
                            end
                        else
                            if game.Players.LocalPlayer.Backpack:FindFirstChild("Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Torch") then
                                equip("Torch")
                                Questtween = toTarget(CFrame.new(1114.87708, 4.9214654, 4349.8501).Position,CFrame.new(1114.87708, 4.9214654, 4349.8501))
                                if (CFrame.new(1114.87708, 4.9214654, 4349.8501).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                    if Questtween then
                                        Questtween:Stop()
                                    end
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1114.87708, 4.9214654, 4349.8501, -0.612586915, -9.68697833e-08, 0.790403247, -1.2634203e-07, 1, 2.4638446e-08, -0.790403247, -8.47679615e-08, -0.612586915)
                                end
                            else
                                Questtween = toTarget(CFrame.new(-1610.00757, 11.5049858, 164.001587).Position,CFrame.new(-1610.00757, 11.5049858, 164.001587))
                                if (CFrame.new(-1610.00757, 11.5049858, 164.001587).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                    if Questtween then
                                        Questtween:Stop()
                                    end
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1610.00757, 11.5049858, 164.001587, 0.984807551, -0.167722285, -0.0449818149, 0.17364943, 0.951244235, 0.254912198, 3.42372805e-05, -0.258850515, 0.965917408)
                                end
                            end
                        end
                    else
                        for i,v in pairs(Workspace.Map.Jungle.QuestPlates:GetChildren()) do
                            if v:IsA("Model") then wait()
                                if v.Button.BrickColor ~= BrickColor.new("Camo") then
                                    repeat wait()
                                        Questtween = toTarget(v.Button.Position,v.Button.CFrame)
                                        if (v.Button.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 150 then
                                            if Questtween then
                                                Questtween:Stop()
                                            end
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.Button.CFrame
                                        end
                                    until not AutoSaber or v.Button.BrickColor == BrickColor.new("Camo")
                                end
                            end
                        end    
                    end
                end
            end 
        end
    end
end)


spawn(function()
    while wait(.1) do
        if Auto_Newworld then
            local Lv = game.Players.LocalPlayer.Data.Level.Value
            if Lv >= 700 and world1 then
				_G.Autofram = false
                if game.Workspace.Map.Ice.Door.CanCollide == true and game.Workspace.Map.Ice.Door.Transparency == 0 then
                    TP2(CFrame.new(4851.8720703125, 5.6514348983765, 718.47094726563))
                    wait(.5)
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("DressrosaQuestProgress","Detective")
                     equip("Key")
                    TP2(CFrame.new(1347.7124, 37.3751602, -1325.6488))
                    wait(3)
                elseif game.Workspace.Map.Ice.Door.CanCollide == false and game.Workspace.Map.Ice.Door.Transparency == 1 then
                    if game:GetService("Workspace").Enemies:FindFirstChild("Ice Admiral [Lv. 700] [Boss]") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == "Ice Admiral [Lv. 700] [Boss]" and v.Humanoid.Health > 0 then
                                repeat game:GetService("RunService").Heartbeat:wait()
                                    pcall(function()
                                        equip(_G.SelectWeapon)
                                        TP(v.HumanoidRootPart.CFrame * CFrame.new(0, 25, 25))
                                        v.HumanoidRootPart.CanCollide = false
                                        v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                        v.HumanoidRootPart.Transparency = .8
                                        game:GetService("VirtualUser"):CaptureController()
                                        game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 870),workspace.CurrentCamera.CFrame)
                                    end)
                                until v.Humanoid.Health <= 0 or not v.Parent
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
                            end
                        end
                    else
                        TP2(CFrame.new(1347.7124, 37.3751602, -1325.6488))
                    end
                else
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
                end
            end
        end
    end
end)

PosGhostYamma = nil
task.spawn(function()
	while wait(.1) do
		if _G.Autoyama then
				if ThreeWorld then
					pcall(function() 
					if game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("EliteHunter", "Progress") < 30 then
						pcall(function()
							local args = {
								[1] = "EliteHunter"
							}
						
							remote = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
							if string.find(remote, "I don't have anything") then
									PosElite = nil
									for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
										if v:IsA("Tool") then
											if string.find(v.Name, 'God') then
												if _G.Autoyama then
													GodSummon = true
												end
											end
										end
									end
									for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
										if v:IsA("Tool") then
											if string.find(v.Name, 'God') then
												if _G.Autoyama then
													GodSummon = true
												end
											end
										end
									end
								if _G.Hopsword and not GodSummon then
									pcall(function()
										for count = math.random(1, math.random(40, 75)), 100 do
											local args = {
											[1] = count
										}
										TableCahce = {}
										remote = game:GetService("ReplicatedStorage").__ServerBrowser:InvokeServer(unpack(args))
										for _i ,v in pairs(remote) do
											for _i2 ,v2 in pairs(v) do
												if tonumber(v['Count']) < 12 then
													if string.find(v['Region'], 'Sing') then
														game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, _i)
													end
												end
											end    
										end    
									end	
									end)
								end
								PosElite = nil
							end
							if string.find(remote, 'Hydra Island') then
		
								EliteHunterName = string.split(string.split(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, 'Defeat')[2], ' ')[2]:gsub(' ', '')
								for _i, v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
										if v:IsA('Model') then
											if string.find(v.Name, EliteHunterName) then
												if (game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Position - v.HumanoiPartdRootPart.CFrame.Position).Magnitude >= 4000 then
													local args = {
														[1] = "requestEntrance",
														[2] = Vector3.new(5742.9599609375, 613.9691772460938, -283.685546875)
													}
													game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
													game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(20,20,20)
												end
												two(v.HumanoidRootPart.CFrame * CFrame.new(-75, 75, 75))
											end
										end
								end
								for _i, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if string.find(v.Name, EliteHunterName) and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then

										repeat wait()
											if not PosElite then
												PosElite = v.HumanoidRootPart.CFrame
											end
											v.HumanoidRootPart.CFrame = PosElite
											equip(_G.SelectWeapon)
											_G.Fastattack = true
											if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
												local args = {
												[1] = "Buso"
												}
												game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
											end
											two(v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0))
												v.Humanoid:ChangeState(14)
												v.HumanoidRootPart.CanCollide = false
												v.Humanoid.WalkSpeed = 0
												v.Humanoid.JumpPower = 0
												v.HumanoidRootPart.Size = Vector3.new(10,10,10)
												if v.Humanoid:FindFirstChild("Animator") then
													v.Humanoid.Animator:Destroy()
												end
												game:GetService'VirtualUser':CaptureController()
												game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
												sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
										until not v:FindFirstChild("Humanoid") or  not v:FindFirstChild("HumanoidRootPart") or not v.Humanoid.Health > 0 or not _G.Autoyama
									end
							end
							end
							if string.find(remote, 'Turtle') then
		
								EliteHunterName = string.split(string.split(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, 'Defeat')[2], ' ')[2]:gsub(' ', '')
								for _i, v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
										if v:IsA('Model') then
											if string.find(v.Name, EliteHunterName) then
												if (game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Position - v.HumanoidRootPart.CFrame.Position).Magnitude >= 4000 then
													-- Script generated by SimpleSpy - credits to exx#9394
														local args = {
															[1] = "requestEntrance",
															[2] = Vector3.new(-12463.6025390625, 378.3270568847656, -7566.0830078125)
														}
														game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
													game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(20,20,20)
												end
												two(v.HumanoidRootPart.CFrame * CFrame.new(-75, 75, 75))
											end
										end
								end
								for _i, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if string.find(v.Name, EliteHunterName) and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
										repeat wait()
											if not PosElite then
												PosElite = v.HumanoidRootPart.CFrame
											end
											v.HumanoidRootPart.CFrame = PosElite
											equip(_G.SelectWeapon)
											_G.Fastattack = true
											if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
												local args = {
												[1] = "Buso"
												}
												game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
											end
											two(v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0))
												v.Humanoid:ChangeState(14)
												v.HumanoidRootPart.CanCollide = false
												v.Humanoid.WalkSpeed = 0
												v.Humanoid.JumpPower = 0
												v.HumanoidRootPart.Size = Vector3.new(10,10,10)
												if v.Humanoid:FindFirstChild("Animator") then
													v.Humanoid.Animator:Destroy()
												end
												game:GetService'VirtualUser':CaptureController()
												game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
												sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
										until not v:FindFirstChild("Humanoid") or  not v:FindFirstChild("HumanoidRootPart") or not v.Humanoid.Health > 0 or not _G.Autoyama
									end
							end
							end
							if not string.find(remote, 'Turtle') and not string.find(remote, 'Hydra Island')  then
		
								EliteHunterName = string.split(string.split(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, 'Defeat')[2], ' ')[2]:gsub(' ', '')
								for _i, v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
										if v:IsA('Model') then
											if string.find(v.Name, EliteHunterName) then
												if (game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Position - v.HumanoidRootPart.CFrame.Position).Magnitude >= 4000 then
													ISLANDPOS = CFrame.new(2181.47559, 29.3805466, -6739.75488, 0.972898781, 3.13111634e-08, -0.231231317, -4.68299923e-08, 1, -6.1625208e-08, 0.231231317, 7.07836563e-08, 0.972898781)
													game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = ISLANDPOS
													game.Players.LocalPlayer.Character.Humanoid.Health = 0
													wait(0.5)
													local args = {
														[1] = "SetSpawnPoint"
													}

													game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
												end
												two(v.HumanoidRootPart.CFrame * CFrame.new(-75, 75, 75))
											end
										end
								end
								for _i, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
									if string.find(v.Name, EliteHunterName) and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
										repeat wait()
											if not PosElite then
												PosElite = v.HumanoidRootPart.CFrame
											end
											v.HumanoidRootPart.CFrame = PosElite
											equip(_G.SelectWeapon)
											_G.Fastattack = true
											if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
												local args = {
												[1] = "Buso"
												}
												game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
											end
											two(v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0))
												v.Humanoid:ChangeState(14)
												v.HumanoidRootPart.CanCollide = false
												v.Humanoid.WalkSpeed = 0
												v.Humanoid.JumpPower = 0
												v.HumanoidRootPart.Size = Vector3.new(10,10,10)
												if v.Humanoid:FindFirstChild("Animator") then
													v.Humanoid.Animator:Destroy()
												end
												game:GetService'VirtualUser':CaptureController()
												game:GetService'VirtualUser':Button1Down(Vector2.new(1280, 672))
												sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
										until not v:FindFirstChild("Humanoid") or  not v:FindFirstChild("HumanoidRootPart") or not v.Humanoid.Health > 0 or not _G.Autoyama
									end
							end
							end
						end)
					else
						wait(two(CFrame.new(5227.13037109375, 8.086737632751465, 1100.6697998046875) * CFrame.new(0, 40,0)))
						for _i, v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if string.find(v.Name, 'Ghost') and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
									if not PosGhostYamma then
										PosGhostYamma = v.HumanoidRootPart.CFrame
									end
									v.HumanoidRootPart.CFrame = PosGhostYamma
									equip(_G.SelectWeapon)
									_G.Fastattack = true
									if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
										local args = {
										[1] = "Buso"
										}
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
									end
									two(v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0))
										v.Humanoid:ChangeState(14)
										v.HumanoidRootPart.CanCollide = false
										v.Humanoid.WalkSpeed = 0
										v.Humanoid.JumpPower = 0
										v.HumanoidRootPart.Size = Vector3.new(10,10,10)
										if v.Humanoid:FindFirstChild("Animator") then
											v.Humanoid.Animator:Destroy()
										end
										sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
							end
					end
					two(CFrame.new(5227.13037109375, 8.086737632751465, 1100.6697998046875) * CFrame.new(0, 40,0))
					if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - (CFrame.new(5227.13037109375, 8.086737632751465, 1100.6697998046875) * CFrame.new(0, 40,0)).Position).Magnitude <= 10 then
						fireclickdetector(game.Workspace.Map.Waterfall.SealedKatana.Handle.ClickDetector)
					end
					end
				end)
				end
			
			end
	end
end)
task.spawn(function()
	while task.wait() do
		if _G.Buddy then
			pcall(function()
				if game:GetService("Workspace").Enemies:FindFirstChild("Cake Queen [Lv. 2175] [Boss]") then
					for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
						if v.Name == "Cake Queen [Lv. 2175] [Boss]" then
							if v:WaitForChild("Humanoid").Health > 0 then
								repeat task.wait()
									if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
										local args = {
											[1] = "Buso"
										}
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
									end
									two(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
									v.HumanoidRootPart.CanCollide = false
									v.HumanoidRootPart.Size = Vector3.new(100, 100, 100)
									game:GetService("VirtualUser"):CaptureController()
									game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
								until not _G.Buddy or not v.Parent or v.Humanoid.Health <= 0
							end
						end
					end
				else
					if (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - CFrame.new(-676.0181274414062, 381.592041015625, -11180.0615234375).Position).Magnitude <= 1500 then
						two(CFrame.new(-676.0181274414062, 381.592041015625, -11180.0615234375))
					else
						bypasstp(CFrame.new(-676.0181274414062, 381.592041015625, -11180.0615234375))
					end
					if _G.Hopsword2 then
						if not game:GetService("ReplicatedStorage"):FindFirstChild("Cake Queen [Lv. 2175] [Boss]") then
							print("HOP !!!")
							pcall(function()
								for count = math.random(1, math.random(40, 75)), 100 do
									local args = {
									[1] = count
									}
									TableCahce = {}
									remote = game:GetService("ReplicatedStorage").__ServerBrowser:InvokeServer(unpack(args))
									for _i ,v in pairs(remote) do
										for _i2 ,v2 in pairs(v) do
											if tonumber(v['Count']) < 12 then
												if string.find(v['Region'], 'Sing') then
													game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, _i)
												end
											end
										end    
									end    
								end
							end)
						end
					end
				end
			end)
		end
	end
end)
task.spawn(function()
	while wait() do
		if _G.Canvender then
			pcall(function()
				if game:GetService("Workspace").Enemies:FindFirstChild("Beautiful Pirate [Lv. 1950] [Boss]") then
					for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
						if v.Name == "Beautiful Pirate [Lv. 1950] [Boss]" then
							if v:WaitForChild("Humanoid").Health > 0 then
								repeat task.wait()
									if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
										local args = {
											[1] = "Buso"
										}
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
									end
									equip(_G.SelectWeapon)
									two(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
									v.HumanoidRootPart.CanCollide = false
									v.HumanoidRootPart.Size = Vector3.new(100, 100, 100)
									game:GetService("VirtualUser"):CaptureController()
									game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
								until not _G.Canvender or not v.Parent or v.Humanoid.Health <= 0
							end
						end
					end
				else
					game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(5314.58203125, 25.419387817383, -125.94227600098))
					wait(3)
					if _G.Hopsword3 then
						if not game:GetService("ReplicatedStorage"):FindFirstChild("Beautiful Pirate [Lv. 1950] [Boss]") then
							print("HOP !!!")
							pcall(function()
								for count = math.random(1, math.random(40, 75)), 100 do
									local args = {
									[1] = count
									}
									TableCahce = {}
									remote = game:GetService("ReplicatedStorage").__ServerBrowser:InvokeServer(unpack(args))
									for _i ,v in pairs(remote) do
										for _i2 ,v2 in pairs(v) do
											if tonumber(v['Count']) < 12 then
												if string.find(v['Region'], 'Sing') then
													game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, _i)
												end
											end
										end    
									end    
								end
							end)
						end
					end
				end
			end)
		end
	end
end)
spawn(function()
	while wait() do
		pcall(function()
			if Auto_Bone then
				if game:GetService("Workspace").Enemies:FindFirstChild("Reborn Skeleton [Lv. 1975]") or game:GetService("Workspace").Enemies:FindFirstChild("Living Zombie [Lv. 2000]") or game:GetService("Workspace").Enemies:FindFirstChild("Domenic Soul [Lv. 2025]") or game:GetService("Workspace").Enemies:FindFirstChild("Posessed Mummy [Lv. 2050]") then
					if game.Players.LocalPlayer.Character.Humanoid.Health > 0 then
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
					end
					for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
						if v.Name == "Reborn Skeleton [Lv. 1975]" or v.Name == "Living Zombie [Lv. 2000]" or v.Name == "Demonic Soul [Lv. 2025]" or v.Name == "Posessed Mummy [Lv. 2050]" then
							if v:WaitForChild("Humanoid").Health > 0 then
								repeat wait()
									if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
										local args = {
											[1] = "Buso"
										}
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
									end
									two(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
									equip(_G.SelectWeapon)
									v.HumanoidRootPart.CanCollide = false
									v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
									game:GetService("VirtualUser"):CaptureController()
									game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
									MainMonBone = v.HumanoidRootPart.CFrame
									BoneMagnet = true
								until Auto_Bone == false or not v.Parent or v.Humanoid.Health <= 0
							end
						end
					end
				else
					BoneMagnet = false
					two(CFrame.new(-9501.64453, 582.052612, 6034.20117))
				end

			end
		end)
	end
end)
spawn(function()
	game:GetService("RunService").Heartbeat:Connect(function()
		pcall(function()
			for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
				if Auto_Bone and BoneMagnet  then
					if (v.Name == "Reborn Skeleton [Lv. 1975]" or v.Name == "Living Zombie [Lv. 2000]" or v.Name == "Demonic Soul [Lv. 2025]" or v.Name == "Posessed Mummy [Lv. 2050]") and (v.HumanoidRootPart.Position - MainMonBone.Position).Magnitude <= 300 then
                        v.Head.CanCollide = false
                        v.HumanoidRootPart.CanCollide = false
                        v.Humanoid.Sit = false
                        v.HumanoidRootPart.Size = Vector3.new(60, 60, 60)
                        v.HumanoidRootPart.CFrame = MainMonBone
                        sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
                        v.Humanoid:ChangeState(14)
                        v.Humanoid:ChangeState(11)
					end
				end
			end
		end)
	end)
end)
spawn(function()
	while game:GetService("RunService").Stepped:wait() do
		character = game.Players.LocalPlayer.Character 
		if Auto_Bone or _G.Auto_Rengoku then
			pcall(function()
				for _, v in pairs(character:GetDescendants()) do
					pcall(function()
						if v:IsA("BasePart") then
						   pcall(function()
							   v.CanCollide = false
						   end)
						end
					end)
				end
			end)
		end
	end
end)

task.spawn(function()
	while wait()  do
		pcall(function()
			if _G.Auto_Dark_Dagger then
				if game:GetService("Workspace").Enemies:FindFirstChild("rip_indra True Form [Lv. 5000] [Raid Boss]") then
					for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
						if v.Name == "rip_indra True Form [Lv. 5000] [Raid Boss]" and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
							pcall(function()
								repeat wait()
									if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
										local args = {
											[1] = "Buso"
										}
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
									end
									two(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
									equip(_G.SelectWeapon)
									v.HumanoidRootPart.CanCollide = false
									v.HumanoidRootPart.Size = Vector3.new(60,60,60)
									game:GetService("VirtualUser"):CaptureController()
									game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
								until not _G.Auto_Dark_Dagger or v.Humanoid.Health <= 0
							end)
						end
					end
				else
					if (game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Position - CFrame.new(-5071.82, 314.541, -3146.16).Position).Magnitude >= 4000 then
						local args = {
							[1] = "requestEntrance",
							[2] = Vector3.new(-5071.82, 314.541, -3146.16)
						}
						
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
						local args = {
							[1] = "GetUnlockables"
						}
						game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))					
					end
				end
			end
		end)
	end
end)

task.spawn(function()
	while wait() do
		pcall(function()
			if _G.Hallow_Scythe then
				if game:GetService("Workspace").Enemies:FindFirstChild('Soul Reaper [Lv. 2100] [Raid Boss]') then
					for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
						if v.Name == 'Soul Reaper [Lv. 2100] [Raid Boss]' or v:FindFirstChild('HumanoidRootPart') or v:FindFirstChild('Humanoid') then
							repeat wait()
								if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
									local args = {
										[1] = "Buso"
									}
									game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
								end
								equip(_G.SelectWeapon)
								two(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
								v.HumanoidRootPart.CanCollide = false
								v.HumanoidRootPart.Size = Vector3.new(60,60,60)
								game:GetService("VirtualUser"):CaptureController()
								game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
							until v.Humanoid.Health <= 0 or not _G.Hallow_Scythe
						end
					end
				else
					pcall(function()
						if not game:GetService("ReplicatedStorage"):FindFirstChild('Soul Reaper [Lv. 2100] [Raid Boss]') then
							if game.Players.LocalPlayer.Backpack:FindFirstChild("Hallow Essence") then
								equip('Hallow Essence')
								if game.Players.LocalPlayer.Character:FindFirstChild("Hallow Essence") then
									two(CFrame.new(-8933.13, 146.822, 6064.42))
									if (game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Position - CFrame.new(-8933.13, 146.822, 6064.42).Position).Magnitude <= 100 then
										game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-8933.13, 146.822, 6064.42)
									else
										two(CFrame.new(-8933.13, 146.822, 6064.42))
									end
								end
							else
								two(CFrame.new(-8722.19629, 141.519562, 6247.646, 0, 0, 1, 0, 1, -0, -1, 0, 0))
								if (game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Position - CFrame.new(-8722.19629, 141.519562, 6247.646, 0, 0, 1, 0, 1, -0, -1, 0, 0).Position).Magnitude <= 20 then
									repeat wait()
										local args = {
											[1] = "Bones",
											[2] = "Buy",
											[3] = 1,
											[4] = 1
										}
										game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
									until game.Players.LocalPlayer.Backpack:FindFirstChild("Hallow Essence") or game.Players.LocalPlayer.Character:FindFirstChild("Hallow Essence") or not _G.AutoHalloween
								else
									two(CFrame.new(-8722.19629, 141.519562, 6247.646, 0, 0, 1, 0, 1, -0, -1, 0, 0))
								end
							end
						end
					end)
				end
			end
		end)
	end
end)



task.spawn(function()
	while wait()  do
		pcall(function()
			if _G.Auto_Rengoku then
				if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild('Hidden Key') then
					equip('Hidden Key')
					if game:GetService("Players").LocalPlayer.Character:FindFirstChild('Hidden Key') then
						if (game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame.Position - CFrame.new(6571.22754, 294.103394, -6967.38184, -0.838688731, 0, -0.544611216, 0, 1, 0, 0.544611216, 0, -0.838688731).Position).Magnitude <= 100 then
							game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(6571.22754, 294.103394, -6967.38184, -0.838688731, 0, -0.544611216, 0, 1, 0, 0.544611216, 0, -0.838688731)
						else
							two(CFrame.new(6571.22754, 294.103394, -6967.38184, -0.838688731, 0, -0.544611216, 0, 1, 0, 0.544611216, 0, -0.838688731))
						end
					end
				else
					if game:GetService("Workspace").Enemies:FindFirstChild('Awakened Ice Admiral [Lv. 1400] [Boss]') then
						for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
							if v.Name == "Awakened Ice Admiral [Lv. 1400] [Boss]" and v:FindFirstChild('HumanoidRootPart') and v:FindFirstChild('Humanoid') and v.Humanoid.Health > 0 then
								pcall(function()
									repeat wait()
										if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
											local args = {
												[1] = "Buso"
											}
											game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
										end
										two(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
										equip(_G.SelectWeapon)
										v.HumanoidRootPart.CanCollide = false
										v.HumanoidRootPart.Size = Vector3.new(100, 100, 100)
										game:GetService("VirtualUser"):CaptureController()
										game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
									until not _G.Auto_Rengoku or v.Humanoid.Health <= 0 or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild('Hidden Key') or game:GetService("Players").LocalPlayer.Character:FindFirstChild('Hidden Key')
								end)
							end
						end
					else
						if (CFrame.new(6383.93066, 296.65329, -6876.88965, 0.509762347, 5.02991782e-09, -0.860315263, -2.02902815e-08, 1, -6.17599616e-09, 0.860315263, 2.06043289e-08, 0.509762347).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude >= 1500 then
							bypasstp(CFrame.new(6383.93066, 296.65329, -6876.88965, 0.509762347, 5.02991782e-09, -0.860315263, -2.02902815e-08, 1, -6.17599616e-09, 0.860315263, 2.06043289e-08, 0.509762347))
						else
							two(CFrame.new(6383.93066, 296.65329, -6876.88965, 0.509762347, 5.02991782e-09, -0.860315263, -2.02902815e-08, 1, -6.17599616e-09, 0.860315263, 2.06043289e-08, 0.509762347))
						end
						if _G.Hopsword4 and not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild('Hidden Key') and not game:GetService("Players").LocalPlayer.Character:FindFirstChild('Hidden Key') then
							if not game:GetService("ReplicatedStorage"):FindFirstChild('Awakened Ice Admiral [Lv. 1400] [Boss]') and not game:GetService("Players").LocalPlayer.Backpack:FindFirstChild('Hidden Key') and not game:GetService("Players").LocalPlayer.Character:FindFirstChild('Hidden Key') then
								pcall(function()
									for count = math.random(1, math.random(40, 75)), 100 do
										local args = {
										[1] = count
										}
										TableCahce = {}
										remote = game:GetService("ReplicatedStorage").__ServerBrowser:InvokeServer(unpack(args))
										for _i ,v in pairs(remote) do
											for _i2 ,v2 in pairs(v) do
												if tonumber(v['Count']) < 12 then
													if string.find(v['Region'], 'Sing') then
														game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, _i)
													end
												end
											end    
										end    
									end
								end)
							end
						end
					end
				end
			end
		end)
	end
end)
spawn(function()
	pcall(function()
		while wait() do
			for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
				if v:IsA("Tool") then
					if v:FindFirstChild("RemoteFunctionShoot") then 
						SelectToolWeaponGun = v.Name
					end
				end
			end
		end
	end)
end)
HealthPersen = 30
spawn(function()
	pcall(function() 
		while wait() do
			if _G.Farm_Mas then
				if _G.SelectMode == "Fruit" then
					if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
						checklevel()
						if (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1500 then
							two(CFrameQ)
						else
							bypasstp(CFrameQ)
						end
						if (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 5 then
							game.ReplicatedStorage.Remotes.CommF_:InvokeServer('StartQuest', NameQuest, QuestLv)
						end
					elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
						if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
							for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v.Name == Ms then
									pcall(function()
										repeat wait()
											checklevel()
											PosMonSkil = v.HumanoidRootPart.CFrame
											HealthMin = v.Humanoid.MaxHealth * HealthPersen/100
											if v.Humanoid.Health <= HealthMin then
												if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
													local args = {
														[1] = "Buso"
													}
													game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
												end
												equip(tostring(game:GetService("Players").LocalPlayer.Data.DevilFruit.Value))
												two(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
												game:GetService("VirtualUser"):CaptureController()
												game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
												UESSKILL = true
												StartMagnetSKILL = true
											else
												UESSKILL = false
												StartMagnetSKILL = true
												if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
													local args = {
														[1] = "Buso"
													}
													game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
												end
												equip(tostring(_G.SelectWeapon))
												two(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
												game:GetService("VirtualUser"):CaptureController()
												game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
											end
										until not _G.Farm_Mas or v.Humanoid.Health <= 0 or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
									end)
								end
							end
						else
							UESSKILL = false
							two(CFramePuk)
						end
					end
				elseif _G.SelectMode == "Gun" then
					if game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false then
						checklevel()
						if (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 1500 then
							two(CFrameQ)
						else
							bypasstp(CFrameQ)
						end
						if (CFrameQ.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 5 then
							game.ReplicatedStorage.Remotes.CommF_:InvokeServer('StartQuest', NameQuest, QuestLv)
						end
					elseif game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == true then
						if game:GetService("Workspace").Enemies:FindFirstChild(Ms) then
							for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
								if v.Name == Ms then
									pcall(function()
										repeat wait()
											checklevel()
											HealthMin = v.Humanoid.MaxHealth * HealthPersen/100
											if v.Humanoid.Health <= HealthMin then
												equip(tostring(SelectToolWeaponGun))
												if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
													local args = {
														[1] = "Buso"
													}
													game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
												end
												com.activeController.hitboxMagnitude = 100000
												local args = {
													[1] = v.HumanoidRootPart.Position,
													[2] = v.HumanoidRootPart
												}
												game:GetService("Players").LocalPlayer.Character[SelectToolWeaponGun].RemoteFunctionShoot:InvokeServer(unpack(args))
												two(v.HumanoidRootPart.CFrame * CFrame.new(0,10,0))
												game:GetService("VirtualUser"):CaptureController()
												game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
											else
												if not game.Players.LocalPlayer.Character:FindFirstChild("HasBuso") then
													local args = {
														[1] = "Buso"
													}
													game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
												end
												equip(tostring(_G.SelectWeapon))
												two(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
												game:GetService("VirtualUser"):CaptureController()
												game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 670),workspace.CurrentCamera.CFrame)
											end
										until not _G.Farm_Mas or v.Humanoid.Health <= 0 or game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Visible == false
									end)
								end
							end
						else
							two(CFramePuk)
						end
					end
				end
			end
		end
	end)
end)
spawn(function()
	pcall(function()
		while wait() do
			if UESSKILL then
				if SKILLZ then
					local args = {
						[1] = PosMonSkil.Position
					}
					game:GetService("Players").LocalPlayer.Character[game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
					game:GetService("VirtualInputManager"):SendKeyEvent(true,"Z",false,game)
					game:GetService("VirtualInputManager"):SendKeyEvent(false,"Z",false,game)
				end
				if SKILLX then
					local args = {
						[1] = PosMonSkil.Position
					}
					game:GetService("Players").LocalPlayer.Character[game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
					game:GetService("VirtualInputManager"):SendKeyEvent(true,"X",false,game)
					game:GetService("VirtualInputManager"):SendKeyEvent(false,"X",false,game)		
				end
				if SKILLC then
					local args = {
						[1] = PosMonSkil.Position
					}
					game:GetService("Players").LocalPlayer.Character[game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
					game:GetService("VirtualInputManager"):SendKeyEvent(true,"C",false,game)
					game:GetService("VirtualInputManager"):SendKeyEvent(false,"C",false,game)	
				end
				if SKILLV then
					local args = {
						[1] = PosMonSkil.Position
					}
					game:GetService("Players").LocalPlayer.Character[game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name].RemoteEvent:FireServer(unpack(args))
					game:GetService("VirtualInputManager"):SendKeyEvent(true,"V",false,game)
					game:GetService("VirtualInputManager"):SendKeyEvent(false,"V",false,game)	
				end
			end	
		end
	end)
end)

spawn(function()
	while wait() do
		if _G.Farm_Mas then
			game:GetService("Players").LocalPlayer.PlayerGui.Notifications:Destroy()
		end
	end
end)


spawn(function()
    while true do game:GetService("RunService").RenderStepped:Wait()
        for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
			checklevel()
            if _G.Farm_Mas and v.Name ~= "Ice Admiral [Lv. 700] [Boss]" and v.Name ~= "Don Swan [Lv. 3000] [Boss]" and v.Name ~= "Saber Expert [Lv. 200] [Boss]" and v.Name ~= "Longma [Lv. 2000] [Boss]" and StartMagnetSKILL and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and (v.HumanoidRootPart.Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 350 then
                if syn then
					if isnetworkowner(v.HumanoidRootPart) then
						v.HumanoidRootPart.CFrame = PosMonSkil
						if v.Humanoid:FindFirstChild("Animator") then
							v.Humanoid.Animator:Destroy()
						end
						sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
					end
				else
					v.HumanoidRootPart.CFrame = PosMonSkil
					if v.Humanoid:FindFirstChild("Animator") then
						v.Humanoid.Animator:Destroy()
					end
					sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius",  math.huge)
				end	
            end
        end
    end
end)

spawn(function ()
	while task.wait() do
		if _G.Rejoinifkick then
			game:GetService("CoreGui").RobloxPromptGui.promptOverlay.ChildAdded:Connect(
				function(a3)
					if
						a3.Name == "ErrorPrompt" and a3:FindFirstChild("MessageArea") and
							a3.MessageArea:FindFirstChild("ErrorFrame")
					 then
						game:GetService("TeleportService"):Teleport(game.PlaceId, LocalPlayer)
					end
				end
			)
		end
	end
end)

_G.Rejoinifkick = true
_G.Z = true
_G.X = true
_G.C = true
_G.V = true
local SettingsTab = win:Tab("Setting")

SettingsTab:Toggle('Rejoin if kick',_G.Rejoinifkick,'6022668898',function(value)
	_G.Rejoinifkick = value
end)

SettingsTab:Toggle('Skill Z',_G.Z,'6022668898',function(value)
	SKILLZ = value
end)
SettingsTab:Toggle('Skill X',_G.X,'6022668898',function(value)
	SKILLX = value
end)
SettingsTab:Toggle('Skill C',_G.C,'6022668898',function(value)
	SKILLC = value
end)
SettingsTab:Toggle('Skill V',_G.V,'6022668898',function(value)
	SKILLV = value
end)
